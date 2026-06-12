---
title: "Very Basic C++ File Opening"
date: 2010-10-14
forum: General Help
---

### Post by jason.hunsaker on 2010-10-14
Hey I am brand new to the entire programming situation. Its coming along pretty well but I'm having trouble when it comes to extracting info from files. Here is my code:

int calories;
    
    ifstream infile;
    infile.open("data.txt");
    infile>> calories;
    cout<< calories;

I know the file is opening because i attatched a if(!infile) later on. But it opens, reads something from the file and displays it as garbage numbers to the output window.

Help!

---

### Post by Sub101 on 2010-10-14
Can you post the "garbage" output?

Is your text file all integers?

---

### Post by jason.hunsaker on 2010-10-14
The only thing in the file is a single integer, 180.

The garbage displayed is -858993460

---

### Post by Sub101 on 2010-10-14
Try adding:

```
infile.open("data.txt", **std::ios::in**);
```

---

### Post by jason.hunsaker on 2010-10-14
No change whatsoever

---

### Post by jason.hunsaker on 2010-10-14
Anything else I can try?

---

### Post by 3Miro on 2010-10-14
I tested the code and it works for me. This means that the error is somewhere else. Please post the entire main.cpp file and wrap it in code tags so we can read it easily.

Here is what works for me:
```

#include <iostream>
#include <fstream>

using namespace std;

int main( int argc, char** argv ){
	
	int calories;

	ifstream infile;
	infile.open("data.txt");

	infile>> calories;
	cout<< calories << endl;
	
	infile.close();
	
	return 0;
	
};

```

Compiled with
```
 g++ main.cpp -o prog 
```

The data file contains only one integer. BTW you made sure it is a text and not a binary file, right?

---

### Post by jason.hunsaker on 2010-10-14
This is all of my code:

```
#include<iostream>
#include<fstream>
using namespace std;

int main(){
    
    int calories;
    
    ifstream infile;
    infile.open("data.txt");
    infile>> calories;
    cout<< calories;
    

    
    
    

    
    
    
    system("PAUSE");
    return 0;
    }
```And yes, it is a text file.

---

### Post by Sub101 on 2010-10-14
Works for me - apart from getting ```
system was not declared in this scope
```

The program and the text file are in the same directory yes?

---

### Post by GregBrannon on 2010-10-14
Just so you know . . . there's an area in the forums called "Programming Talk" for these kind of questions.

It's [here.]("http://ubuntuforums.org/forumdisplay.php?f=39")

---

### Post by jason.hunsaker on 2010-10-14
Thanks Greg I'll check it out.

Sub101- I guess it must not be. I just created a regular folder on the hard drive. How do I get it in the same directory as the project?

---

### Post by Sub101 on 2010-10-14
> **jason.hunsaker said:**
> 
Sub101- I guess it must not be. I just created a regular folder on the hard drive. How do I get it in the same directory as the project?

Sorry I dont understand what you mean?

What I would is create a folder and create the cpp file and txt file in the new folder.

---

### Post by jason.hunsaker on 2010-10-14
Ok, thanks I got it.

Originally I had the file saved on the hard drive. As soon as I created a new one in the same file as the cpp folder as you suggested, it worked. 

Thank you, I really appreciate the help.
Btw is there a way to close this thread since it is resolved?

---

### Post by Sub101 on 2010-10-14
You can mark it as solved. - the end of this thread shows how: [http://ubuntuforums.org/showthread.php?t=954716](http://ubuntuforums.org/showthread.php?t=954716)

Have fun programming.

---

