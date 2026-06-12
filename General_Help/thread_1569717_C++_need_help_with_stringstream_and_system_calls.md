---
title: "C++: need help with stringstream and system calls"
date: 2010-09-07
forum: General Help
---

### Post by d3v1150m471c on 2010-09-07
I'm trying to use system to call echo and pass variables to it. That was a success. The problem is the variables inside the while-loop i wrote cannot be manipulated. Can someone tell me what I'm doing wrong here?

here's the code:
```

#include <iostream>
#include <stdlib.h>
#include <string>
#include <sstream>

using namespace std;

int main() {

string array[64];
array[0]="a";
array[1]="b";
array[2]="c";
array[3]="d";
array[4]="e";
array[5]="f";
array[6]="g";
array[7]="h";
array[8]="i";
array[9]="j";
array[10]="k";
array[11]="l";
array[12]="m";
array[13]="n";
array[14]="o";
array[15]="p";
array[16]="q";
array[17]="r";
array[18]="s";
array[19]="t";
array[20]="u";
array[21]="v";
array[22]="w";
array[23]="x";
array[24]="y";
array[25]="z";
array[26]="A";
array[27]="B";
array[28]="C";
array[29]="D";
array[30]="E";
array[31]="F";
array[32]="G";
array[33]="H";
array[34]="I";
array[35]="J";
array[36]="K";
array[37]="L";
array[38]="M";
array[39]="N";
array[40]="O";
array[41]="P";
array[42]="Q";
array[43]="R";
array[44]="S";
array[45]="T";
array[46]="U";
array[47]="V";
array[48]="W";
array[49]="X";
array[50]="Y";
array[51]="Z";
array[52]="0";
array[53]="1";
array[54]="2";
array[55]="3";
array[56]="4";
array[57]="5";
array[58]="6";
array[59]="7";
array[60]="8";
array[61]="9";
array[62]="0";
int X, Y, Z;

X = 0;
Y = 0;
Z = 0;

stringstream cmd;
cmd << "echo " << array[Z] << array[Y] << array[X];


while ( Z < 63 )
{
system(cmd.str().c_str());
//cout << array[Z] << array[Y] << array[X] << endl;
     if (X > 61)
     {
     X = 0;
     Y = Y + 1;
     }

     if (Y > 61)
     {
     Y = 0;
     Z = Z + 1;
     }

X = X + 1;
}
return(0);
}


```

---

### Post by Vaphell on 2010-09-07
but the variables are manipulated, just cout X Y Z
the problem i see is that you defined the cmd as echo array[0] array[0] array[0]
move cmd part into the while loop so the cmd is recreated for updated values of XYZ

---

### Post by spjackson on 2010-09-07
> **d3v1150m471c said:**
> I'm trying to use system to call echo and pass variables to it. That was a success. The problem is the variables inside the while-loop i wrote cannot be manipulated. Can someone tell me what I'm doing wrong here?

What variables can't be manipulated? You are successfully incrementing X, Y and Z.

However, instead of this
```

stringstream cmd;
cmd << "echo " << array[Z] << array[Y] << array[X];


while ( Z < 63 )
{
system(cmd.str().c_str());

```don't you mean the following?
```

while ( Z < 63 )
{
stringstream cmd;
 cmd << "echo " << array[Z] << array[Y] << array[X];
 
system(cmd.str().c_str());

```

---

### Post by d3v1150m471c on 2010-09-07
you guys are awesome. thanks

---

### Post by d3v1150m471c on 2010-09-07
if i use 
```
cout << array[Z] << array[Y] << array[X] << endl;
```instead of
```

system(cmd.str().c_str());
cmd << "echo " << array[Z] << array[Y] << array[X] << endl;

```i get the correct output but i need to be able to do this with "system". echo was just a test before i put more effort into the code.

currently my output looks like this while using the snippet above in the while-loop. if you compile my code using just the cout command you'll see the new problem i face
```

aaa
aaa
aab
aaa
aab
aac
aaa
aab
aac
aad
aaa
aab
aac
aad
aae
aaa
aab
aac
aad
aae
aaf
aaa
aab
aac
aad
aae
aaf
aag
aaa

```

for whatever reason the array keeps resetting and starts back at "a" before it can reach a new letter. bah

---

### Post by spjackson on 2010-09-07
The code I posted before did essentially the right thing, so I don't really follow why you changed it to do the wrong thing in various different ways.

However, I didn't fix the looping bugs in your do-it-yourself loop. So let's do it in a less error-prone way:

```

for (Z=0; Z<63; Z++)
{
   for (Y=0; Y<63; Y++)
   {
      for (X=0; X<63; X++)
      {
         string cmd;
         cmd = string("echo ") + array[Z] + array[Y] + array[X];
         system(cmd.c_str());
      }
   }
}

```By the way, you have
```

array[52]="0";
.
.
array[62]="0";

```So you'll get both 0s in your output.

Calling system() 62*62*62 times will always be somewhat slow.

---

### Post by d3v1150m471c on 2010-09-07
thanks again. i did essentially the same thing in a couple other languages but you simply cannot match the speed of C++. The problem is i can count on 1 hand the things i've written in it. i'll give the for-loop a shot and see how it goes.

---

### Post by d3v1150m471c on 2010-09-07
that was gorgeous. it works perfect.

---

