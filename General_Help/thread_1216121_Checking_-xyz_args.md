---
title: "Checking -xyz args"
date: 2009-07-17
forum: General Help
---

### Post by Muscovy on 2009-07-17
I'm trying to build a program that can apply arguments from command line. I know how to take a string and find things in it, so I can tell that the person has entered x, y, and z with that... but only with strings.

  Do I convert argv to a string or adapt:
if((i = argc.find("cat", 0)) && (i != argc::npos) && (i = argc.find("cat", i)))
to use char? Neither? And how do I do it?



PS - This is in C++

---

### Post by Muscovy on 2009-07-17
```

#include <iostream>
#include <string>

using namespace std;

int main( int argc, char** argv )
{

string input;
int i = 0;

input =+ argv[1];

cout << input ;

if((i = input.find("cat", 0)) && (i != string::npos) && (i = input.find("cat", i)))
{
    cout << "You're a kitty!\n" ;
    //i++;  // Move past the last discovered instance to avoid finding same
          // string
}

}

```
  Ok, everything works, except the argument must be encased in other things.
  For example, program cat doesn't work, program -cat- does.

---

