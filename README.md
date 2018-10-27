
		/*
		Input:
		1st number = 9x^2 +        1990x^0
		2nd number = 9x^2 + 7x^1 + 8x^0
		Output:
		18x^2 + 7x^1 + 1998
		Happy Birthday!!!
		*/

		//Add Two Polynomials using Linked List!
		//Using C++ programming!

		#include<iostream>
		using namespace std;

		// Node structure containing power and coefficient of variable 
		struct _Node {
			int coeff;
			int pow;
			struct _Node *next;
		};
		typedef struct _Node Node;

		// Function to create new node
		void Create_Node(int coeff, int pow, Node **temp) {
			Node *z;
			Node *r;
			z = *temp;
			if (z == NULL) {
				r = new Node[sizeof(Node)];
				r->coeff = coeff;
				r->pow = pow;
				*temp = r;
				r->next = new Node[sizeof(Node)];
				r = r->next;
				r->next = NULL;
			}
			else {
				r->coeff = coeff;
				r->pow = pow;
				r->next = new Node[sizeof(Node)];
				r = r->next;
				r->next = NULL;
			}
		}

				// Function Adding two polynomial numbers 
				void addPoly(Node *Poly1, Node *Poly2, Node *Poly) {
				while ((Poly1->next) && (Poly2->next)) {
				//if power of 1 st number is greater than power of 2 nd number, store 1 st!
				//move pointer to next pointer!
				if ((Poly1->pow) > (Poly2->pow)) {
					Poly->coeff = Poly1->coeff;
					Poly->pow = Poly1->pow;
					Poly1 = Poly1->next;
				}

				//if power of 1 st number is less than power of 2 nd number, store 2 nd!
				//move pointer to next pointer!
				else if ((Poly1->pow) < (Poly2->pow)) {
					Poly->coeff = Poly2->coeff;
					Poly->pow = Poly2->pow;
					Poly2 = Poly2->next;
				}

				// If power of both polynomial numbers is same then add their coefficients 
				else {
					Poly->coeff = (Poly1->coeff) + (Poly2->coeff);
					Poly->pow = Poly1->pow;
					Poly1 = Poly1->next;
					Poly2 = Poly2->next;
				}

				//Create new node!
				Poly->next = new Node[sizeof(Node)];
				Poly = Poly->next;
				Poly->next = NULL;
			}
			while ((Poly1->next) || (Poly2->next)) {
				if (Poly1->next) {
					Poly->coeff = Poly1->coeff;
					Poly->pow = Poly1->pow;
					Poly1 = Poly1->next;
				}
				if (Poly2->next) {
					Poly->coeff = Poly2->coeff;
					Poly->pow = Poly2->pow;
					Poly2 = Poly2->next;
				}
				Poly->next = new Node[sizeof(Node)];
				Poly = Poly->next;
				Poly->next = NULL;
			}
		}

		// Display Linked list
		void displayPoly(Node *Poly) {
			while (Poly->next) {
				cout << Poly->coeff << "x^" << Poly->pow;
				Poly = Poly->next;
				if (Poly->next) {
					cout << " + ";
				}
			}
			cout << endl;
		}

		// Driver  program 
		int main() {
			char ch;
			int coeff;
			int pow;
			Node *Poly1 = NULL;
			Node *Poly2 = NULL;
			Node *Poly = NULL;

			//Create first polinomial!
			cout << "Enter First Polinomial!" << endl;
			do {
				cout << "Enter coefficient and power: ";
				cin >> coeff >> pow;
				Create_Node(coeff, pow, &Poly1);
				cout << "Do you want to continue!(Y/N)? ";
				cin >> ch;
			} while (ch == 'Y' || ch == 'y');

			//Create second polynomial!
			cout << "Enter Second Polinomial!" << endl;
			do {
				cout << "Enter coefficient and power: ";
				cin >> coeff >> pow;
				Create_Node(coeff, pow, &Poly2);
				cout << "Do you want to continue!(Y/N)? ";
				cin >> ch;
			} while (ch == 'Y' || ch == 'y');

			//Display first polynomial!
			cout << "1st number = ";
			displayPoly(Poly1);
			cout << endl;

			//Display first polynomial!
			cout << "2nd number = ";
			displayPoly(Poly2);
			cout << endl;

			Poly = new Node[sizeof(Node)];
			//Add two Polynomials!
			addPoly(Poly1, Poly2, Poly);

			//Display result!
			cout << "Result = ";
			displayPoly(Poly);
			system("pause");
			return 0;
		}
