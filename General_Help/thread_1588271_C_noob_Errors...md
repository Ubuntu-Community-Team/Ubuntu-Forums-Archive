---
title: "C noob Errors.."
date: 2010-10-04
forum: General Help
---

### Post by v1ad on 2010-10-04
i am still a noob in the C language and need help figuring out what exactly am i doing wrong. tried google.. here are my errors.

errors
```

gcc -Wall -c "lab.c" (in directory: /home/vlad/Dropbox/C/lab5)
lab.c: In function ‘main’:
lab.c:15: warning: implicit declaration of function ‘menu’
lab.c:16: warning: implicit declaration of function ‘add’
lab.c: In function ‘menu’:
lab.c:29: warning: implicit declaration of function ‘system’
lab.c: At top level:
lab.c:41: warning: conflicting types for ‘add’
lab.c:16: note: previous implicit declaration of ‘add’ was here
lab.c: In function ‘add’:
lab.c:47: warning: implicit declaration of function ‘getint’
lab.c:50: warning: implicit declaration of function ‘getreal’
lab.c:52: warning: implicit declaration of function ‘show’
lab.c: At top level:
lab.c:110: error: conflicting types for ‘getreal’
lab.c:50: note: previous implicit declaration of ‘getreal’ was here
lab.c:138: warning: conflicting types for ‘show’
lab.c:52: note: previous implicit declaration of ‘show’ was here
Compilation failed.

```

source code
```


/*#******************************************************************#*/
/*
	Vladi
	Lab# 5
	Compiler: GCC
*/

#include <stdio.h>
#include <string.h>
/*====================================================================*/
double total(int a, double b);
int main() {
	int more = 0;O
	do {
		switch(menu()) {
			case 1: add(); break;
			case 2:
			case 3:
			case 4: printf("\n Not implemented"); break;
			case 5: more ++; break;
			default: printf("\n Error Occurred\a");
		}O
	}
	while (more == 0);
	return 0;
}
/*====================================================================*/
int menu() {
	system("clear");
	int choice;
	printf("Sierra Sporting Goods \n\n");
	printf("1 = Add a record \n");
	printf("2 = Report\n");
	printf("3 = Delete a record\n");
	printf("4 = Change a record\n");
	printf("5 = Quit");
	scanf("%d%*c", &choice);
	return(choice);OO
}
/*====================================================================*/
void add() {	
	char contin;
	do {
		int number=0, amount=0, type=0, i=0;
		double cost=0, price=0;
		printf("Sierra Sporting Goods \n\n");
		number = getint(1);
		type = getint(2);
		amount = getint(3);
		cost = getreal(1);
		price = getreal(2);
		show(number, amount, cost, price);
		printf("\nContinue: (Y/N) ");
		scanf("%c%*c", &contin);
		do {
			if (contin == 'Y' || contin == 'y' || contin == 'N' || contin == 'n') {
			i = 1;
			}
			else {
			printf("Please Enter a Y or N");
			printf("\nContinue: (Y/N) ");
			scanf("%s%*c", &contin);
			i = 0;O
			}
		}
		while (i < 1);
	}
	while (contin == 'Y' || contin == 'y');
}	
/*====================================================================*/
int getint(int n) {
	int i=0;
	if (n == 1) {
		printf("Enter the product number: ");
		scanf("%d%*c", &i);
		while (i <= 0 || i >= 1000) {
			printf("Product # needs to be between 1 and 999\n");
			printf("Enter the product number: ");
			scanf("%d%*c", &Oi);
		}
	}
	else if (n == 2) {
		printf("Enter the  product type: ");
		scanf("%d%*c", &i);
		while (i <= 0 || i >= 6) {
			printf("The product type needs to be between 1 and 5\n");
			printf("Enter the  product type: ");
			scanf("%d%*c", &i);
		}
	}
	else if (n == 3) {O
		printf("Enter the quantity: ");
		scanf("%d%*c", &i);
		while (i <= 0 || i >= 51) {
			printf("The quantity needs to be between 1 & 50\n");
			printf("Enter the quantity: ");
			scanf("%d%*c", &i);
		}
	}
	else {
		system("clear");
		printf("/n Unknown erro#include <stdlib.h>r occurred(getint function) /n");
		main();
	}
	return(i);
}

/*====================================================================*/

double getreal(int n) {
	double i;
	if (n == 1) {
		printf("Enter the cost: ");	
		scanf("%lf%*c", &i);
		while (i <= 4 || i >= 901) {
			printf("The cost needs to be between $5 and $900\n");
			printf("Enter the cost: ");	
			scanf("%lf%*c", &i);
		}
	}
	else if (n == 2) {
		printf("Enter the price: ");	
		scanf("%lf%*c", &i);
		while (i <= 5 || i >= 1001) {
			printf("Prince needs to be between $6 & $1000\n");
			printf("Enter the price: ");	
			scanf("%lf%*c", &i);
		}
	}
	else {
		system("clear");
		printf("/n Unknown error occurred(getreal function) /n");
		main();
	}
	return(i);
}
/*====================================================================*/
void show(int product, int amount, double cost, double price) {
	int totalamount;
	double totalPrice=0, totalCost=0, totalprofit=0, profit=0, allcosts=0, allprices=0;
	allcosts = total(amount, cost);
	allprices = total(amount, price);
	profit = allprices - allcosts;
	totalprofit += profit;
	totalPrice += allprices;
	totalCost += allcosts;
	totalamount += amount;
	printf("Total all costs: %.2lf.\n", allcosts);
	printf("Total all prices: %.2lf.\n", allprices);
	printf("Total profit: %.2lf.\n", profit);
	printf("\n\nTotal count of products: %d.\n", totalamount);
	printf("Total all prices: %.2lf.\n", totalPrice);
	printf("Total all costs: %.2lf.\n", totalCost);
	printf("Total profit: %.2lf.\n", totalprofit);
}
/*====================================================================*/
double total(int a, double b) {
	double i;
	i = (a * b);
	return(i);
}

/*#******************************************************************#*/

```

---

### Post by spjackson on 2010-10-04
You should declare prototypes for your functions before you call them. You have done this with total(), so do the same for the rest of your functions.

The Programming Talk forum  [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39) is useful for this type of problem.

---

### Post by Zanthir on 2010-10-04
Declaring prototypes is normally done in the header file, which you need to include in your c file.

---

### Post by v1ad on 2010-10-04
Ty all solved by adding this to the top:
```

double total(int a, double b), getreal(int n);
int menu(), getint(int n);
void add(), show(int product, int amount, double cost, double price);

```

---

