---
title: "String manipulation"
date: 2010-07-21
forum: General Help
---

### Post by soft-e on 2010-07-21
Hello,
 
I have the folloowing three lines
 
a;b;c;d;e
i;j;k
s;t;u;v
 
I'd like to print out each string with their individual fields and the field seperator execpt the last field. There could be any number of fields in a line. So for the above example the output shoudl be:
 
a;b;c;d
i;j
s;t;u
 
Please assist.
 
Thanks
soft-e

---

### Post by cph05a on 2010-07-21
it's not really clear what exactly you're asking for here. I can assume this is a programming assignment, but what are you calling a field, what language, is this an assignment for school?

---

### Post by rubylaser on 2010-07-21
It looks like your not really separating with a delimiter, but your just hacking off the last semi-colon and character, you can do that easily with sed.
```
echo "a;b;c;d;e" | sed 's/.\{2\}$//'
a;b;c;d

```

Here's how you could use that...
```
cat test.txt |  sed 's/.\{2\}$//'
```
```
a;b;c;d
i;j
s;t;u

```

Finally, have it dump out an edited file.
```
cat original_data.txt |  sed 's/.\{2\}$//' > modified_data.txt
``` 
Hope that helps.

---

### Post by vandorjw on 2010-07-21
I don't think using sed will work all the time.

He called characters "fields" and said that there could be any number of fields per line. And Sed works great until there are more Characters per field. Then it wont work anymore...

example:
-aab;adf;adfew;fa;adfafas

this would become

-aab;adf;adfew;fa

What you need to do is this (in the language of your choosing)
A string is really an array of characters. So, go to the end of the array, and if it does not equal the field delimiter, delete the character and go the the next character. if it is equal to the field delimiter, delete it also, and move on the the next array.

if you run out of arrays/strings, you are done.

if you need an example on how to do this more specifically, let me know.

Cheers - CC7

---

### Post by vandorjw on 2010-07-21
```

#include <iostream>

int main(){
using namespace std;

string string_1;
string string_2;
string string_3;

cout << "Please fill 3 strings with a bunch of fields" << endl;

getline(cin, string_1, '\n');
getline(cin, string_2, '\n');
getline(cin, string_3, '\n');

char delimiter = ';';

int lastDel=string_1.rfind(delimiter);
string_1.erase(lastDel);

lastDel=string_2.rfind(delimiter);
string_2.erase(lastDel);

lastDel=string_3.rfind(delimiter);
string_3.erase(lastDel);


cout << string_1 << endl << string_2 << endl << string_3 << endl;

return 0;
}

```

**Here is the result**

Please fill 3 strings with a bunch of fields
abc;def;ghi;jklm
nop;qr;st
uv;w;x;yz

abc;def;ghi
nop;qr
uv;w;x

I hope this is what you were looking for. The code should be reasonably self-explanatory. If you are not sure about something, just google "C++ string manipulation" 
Cheers - CC7

---

### Post by rubylaser on 2010-07-21
I was just trying to solve the example he showed, but based on what you said (which makes sense), how about just doing this in bash with a one-liner.
```
cat test.txt | rev | cut -d ";" -f2- | rev > output.txt
```
This takes the line reverses in takes everything from the first ; delimiter to the end, and then reverses it back, easy as pie :)

Example in action:
```
$ cat test.txt
aab;adf;adfew;fa;adfafas
aab;adf;adfew;fa;adf
aab;adf;adfew;fa
```

```
$ cat test.txt | rev | cut -d ";" -f2- | rev
aab;adf;adfew;fa
aab;adf;adfew;fa
aab;adf;adfew
```

Hope that helps.

---

### Post by vandorjw on 2010-07-21
C++ cannot compete with Black Magic ;)

*mumbles to self* One line....not possible...one line... *mumble*

---

