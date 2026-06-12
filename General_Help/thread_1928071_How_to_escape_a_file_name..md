---
title: "How to escape a file name."
date: 2012-02-19
forum: General Help
---

### Post by corrado33 on 2012-02-19
So I'm writing a script that moves files from one computer to another with scp.  However, those files aren't named the same, sometimes they have spaces, sometimes they don't.  There is no set length, basically the file name could be anything.  
 
So I need to escape the string inside the script.
 
I tried (printf "%g" $myString) but it gets rid of all of the spaces.
 
Example.
 
myVar='My file is aweome(Yes it [is]).txt'
myVar2=$(printf "%q" $myVar)
 
echo $myVar2
 
Myfileisawesome\(Yesit\[is\]\).txt
 
Basically, it gets rid of the spaces and escapes the rest of the characters.  I need it to KEEP the spaces so I can use the variable to refer to a file.  
 
If you have an answer, could you point me to where I could learn why your answer works?  I want to learn, not just get the answer. 
 
Thanks!

---

### Post by corrado33 on 2012-02-19
I feel dumb.  (Why do I always find the answer after I've given up and posted a quesion?)
 
I need to use 
 
myVar2=(printf "%q" "$myVar")
 
Notice the extra weak quotes around the %myVar.
 
Thanks anyway. :P

---

### Post by kevdog on 2012-02-19
Depending on the variable I would even try

"${myvar}"

---

