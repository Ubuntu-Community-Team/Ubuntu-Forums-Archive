---
title: "Reading data from a file and printing it, in C programming language"
date: 2011-06-30
forum: General Help
---

### Post by linux_trojan on 2011-06-30
I am trying to read a file and print the data to the screen. This is what the code looks like so far.

    Code:

    #include <stdio.h>
    #include <string.h>
    #include <stdlib.h>

    char a[50];
    int i;



    FILE *fp;

    int main()
    {


    fp = fopen("PSV101data.rtf", "r");
    for (i=1; i <= 47; i++)
    {fscanf(fp, "%s\n", a[i]);
    printf("%s/n", a[i]);}
    fclose(fp);

    return 0;
    }


    This is the output

    (null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/n(null)/

    I am trying to just read one line at a time and output one line at a time. Any suggestions would be appreciated.

---

### Post by Dominic Gunn on 2011-06-30
Hey Man,

Looking for a first attempt and you seem to be on the right lines, ever think of trying to use fget()? Try something like this

[PHP]
#include <stdio.h>

int main() {
  FILE *fp;
  char line[100];

// open the file for reading
 fp = fopen("PSV101data.rtf", "r");
// Loop through all lines in the file until we hit the last one
  while( fgets(line, sizeof(line), fp) != NULL ) {
    // Print the line data
    printf("Line %s", line);  
  }
 // Close the file we're done with it
  fclose(infile); 
}
 [/PHP]

Give that a shot and let me know what happens! My c's a bit hazy but I think that's good to go!

---

### Post by linux_trojan on 2011-06-30
hey man, that worked. I will study all the ends and outs of it and get a handle on it.  Thank you.

Oh, I forgot to mention, the last line should be "fclose(fp).

---

### Post by Dominic Gunn on 2011-06-30
Yeah, sorry about that! Named it in accordance with how I would've named that variable; sorry about that! Glad to hear it's working. :)

---

