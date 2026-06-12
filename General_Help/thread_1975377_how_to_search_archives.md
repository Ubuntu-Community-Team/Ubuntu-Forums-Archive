---
title: "how to search archives  ?"
date: 2012-05-07
forum: General Help
---

### Post by winzip on 2012-05-07
I  have many  **JAR  **archives  in  **lib **folder .

I  want to print out JAR file names which contains   file    [B]abc.class

[/B]Whats the solution ?


System :  Ubuntu 10.04  - Server OS ( no GUI)[U]

Example:[/U][U]

Input [/U][B]_:   _

[/B]searchKey = [B] abc.class

[/B]search Folder=  [B]/home/user/lib


[/B]_Output_[B]_:_

match found 

abc.class [/B]found in[B]   zxzbcc.jar  ,  ewtf.jar  ,  yuop.jar   


[/B]

---

### Post by albandy on 2012-05-07
cd /home/user/lib
for i in *.jar 
do RESULT=$(unzip -l "$i" | grep abc.class) 
if [ "$RESULT" != "" ] 
then 
echo $i 
fi 
done

---

### Post by winzip on 2012-05-07
> **albandy said:**
> cd /home/user/lib
for i in *.jar 
do RESULT=$(unzip -l "$i" | grep abc.class) 
if [ "$RESULT" != "" ] 
then 
echo $i 
fi 
done

Is this script ?  Or I just need to type inline ?
Could you plesse correct it if its a script.

---

### Post by albandy on 2012-05-07
You can type it or save it to a file and run 
sh filename

---

### Post by winzip on 2012-05-07
> **albandy said:**
> You can type it or save it to a file and run 
sh filename

I,ll prefer typing then.

How do i type multiple line in command console ?
Do i need semicolon after each line ?

---

### Post by albandy on 2012-05-07
You can write it line by line. No semicolon needed or you can write it this way:
cd /home/user/lib; for i in *.jar; do RESULT=$(unzip -l "$i" | grep class); if [ "$RESULT" != "" ]; then echo $i; fi; done

---

### Post by winzip on 2012-05-07
> **albandy said:**
> You can write it line by line. No semicolon needed or you can write it this way:
cd /home/user/lib; for i in *.jar; do RESULT=$(unzip -l "$i" | grep class); if [ "$RESULT" != "" ]; then echo $i; fi; done

I'll prefer line by line. So there will be 6 lines in command line.  Dont i need a semicolonat lst line?  Just hitting enter will execute this ?

---

