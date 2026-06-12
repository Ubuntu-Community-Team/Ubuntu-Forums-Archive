---
title: "how to select lines containing word and copy to another file"
date: 2011-05-31
forum: General Help
---

### Post by keevill on 2011-05-31
I am trying to find a way to search a text file for a certain keyword and then select each line containing the word , copy and paste these lines into another text file.
I can do this easily with UltraEdit but I cannot figure out how to do it in Jedit or Scite.
Anyone able to help ?
-keevill-

---

### Post by linuxinstalledfromhdd on 2011-05-31
I can do it with notepad++ but that is all I ever really use.

---

### Post by Doug S on 2011-05-31
grep will do it. In a terminal window in the directory containing the text file (input.txt) enter the following command:
```
grep keyword input.txt >output.txt
```Noting that "keyword is case sensitive, use the -i switch if you want to ignore case. Also if the search string is multiple words then surround it in quotes, i.e.:
```
grep -i "keyword string including spaces" input.txt >output.txt
```

---

### Post by keevill on 2011-05-31
> **Doug S said:**
> grep will do it. In a terminal window in the directory containing the text file (input.txt) enter the following command:
```
grep keyword input.txt >output.txt
```Noting that "keyword is case sensitive, use the -i switch if you want to ignore case. Also if the search string is multiple words then surround it in quotes, i.e.:
```
grep -i "keyword string including spaces" input.txt >output.txt
```

Well ...yes ..it will but it's not really easy to do link in Gui especially if the input text file contains many characters.
-keevill-

---

### Post by Lifeboat on 2011-05-31
I don't understand your answer, specifically your use of "link". What link?

Grep will search your entire file for you, in one terminal line of code.

Do you mean that you are searching for many words or phrases, and not just one?

---

### Post by keevill on 2011-05-31
> **Lifeboat said:**
> I don't understand your answer, specifically your use of "link". What link?

Grep will search your entire file for you, in one terminal line of code.

Do you mean that you are searching for many words or phrases, and not just one?

whoops ! I don't understand ME either :-)
I meant to type "it's not really easy to do IN in Gui especially if the input text file contains many characters."
( dunno how link got put in there )
To further clarify: if the input file is long and it has to be typed it's tedious. 
Since I have many to do, the UltraEdit ability to open file , type in the word to search and list lines containing is effortless.
I agree , of course that grep will do the job however, coming from Windoze, and being used to GUI , I really prefer to do it in GUI if possible.
Thx for your kind help ( and I'll preview this post before sending :-) )

-keevill-

---

