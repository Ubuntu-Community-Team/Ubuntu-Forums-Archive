---
title: "C language help ask"
date: 2011-04-22
forum: General Help
---

### Post by gbrunati on 2011-04-22
I want to print a text using it's var name call, but what I get is the name itself. Help me, please...

#include <stdio.h>
#include <string.h>

int main()
{
char chvar[9];
char *var_name = "blablablsblablablablsblablablablsblablblblaaablablablsbla.\n";

	strcpy(chvar, "var_name");
	printf("%s\n", chvar);

	return 0;
}

It prints "var_name" and I want:

"blablablsblablablablsblablablablsblablblblaaablablablsbla.\n", instead;

thanks in advance for your help.

---

### Post by TeoBigusGeekus on 2011-04-22
Try with this
```
#include <stdio.h>
#include <string.h>

 int main()
 {
 char chvar[9];
 char *var_name = "blablablsblablablablsblablablablsblablblblaaablab lablsbla.\n";

 strcpy(chvar, [COLOR="Red"]var_name[/COLOR]);
 printf("%s\n", chvar);

 return 0;
 }
```

The code will of course cause a segmentation fault because chvar doesn't have enough space for your string - I don't know if that's what you wanted.

---

### Post by gbrunati on 2011-04-22
Thanks for your reply. It's not exactly wath I want, &#928;&#945;&#953;&#967;&#957;&#943;&#948;&#953;; I need to select and print one from a group of texts, and var_name is constructed in a separate subroutine, so it is the name of the choosen text variable (var_name in this case). 

My problem is that argument 2 in the "strcpy" is recognized as the name of the var_name string and I want the variable itself, so it prints the corresponding text.

---

### Post by rshinde70 on 2011-04-22
> **gbrunati said:**
> Thanks for your reply. It's not exactly wath I want, &#928;&#945;&#953;&#967;&#957;&#943;&#948;&#953;; I need to select and print one from a group of texts, and var_name is constructed in a separate subroutine, so it is the name of the choosen text variable (var_name in this case). 

My problem is that argument 2 in the "strcpy" is recognized as the name of the var_name string and I want the variable itself, so it prints the corresponding text.

Try 

```
man strcpy
```

---

### Post by holiday on 2011-04-22
> **gbrunati said:**
> Thanks for your reply. It's not exactly wath I want, &#928;&#945;&#953;&#967;&#957;&#943;&#948;&#953;; I need to select and print one from a group of texts, and var_name is constructed in a separate subroutine, so it is the name of the choosen text variable (var_name in this case). 

My problem is that argument 2 in the "strcpy" is recognized as the name of the var_name string and I want the variable itself, so it prints the corresponding text.


You have to remove the quotes from the variable name.

---

### Post by gbrunati on 2011-04-22
Trying to explain me more, this is the code with more details:

#include <stdio.h>
#include <string.h>
char chnitxpr[9];
char* fPlnNcs (pto_cel pcpto);

int main()
{
char chvar[9];
char *chNepC01 = "01blablablsblablablablsblablablablsblablblblaaabla0101010101.\n";
char *chNepC02 = "02blablablsblablablablsblablablablsblablblblaaabla0202020202.\n";
char *chNepC03 = "03blablablsblablablablsblablablablsblablblblaaabla0303030303.\n";
...
/* fPlnNcs(sol) = chnitxpr could be chNepC01, chNepC02, chNepC03...  chNepC0N */

	fPlnNcs(sol); /* this is a string */
	strcpy(chvar, fPlnNcs(sol));
	printf("%s\n", chvar);

	or...

	fPlnNcs(sol); /* this is a string */
	strcpy(chvar, chnitxpr);
	printf("%s\n", chvar); /* I want to print the text, but prints the name of the variable */

	return 0;
}

char* fPlnNcs (pto_cel pcpto) /* Ubica punto celeste en casa (21 de abril 2011)*/
{
...
...
	return chnitxpr; 
}

---

