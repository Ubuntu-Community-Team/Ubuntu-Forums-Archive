---
title: "How can I batch edit text files"
date: 2009-07-23
forum: General Help
---

### Post by 007casper on 2009-07-23
Hi. 

I have over two hundred folders that has bunch text files that needs to be edited with the same set of words.  

here is a dummy example - the original text file:
Hello! How are you?

the revised version:
hello! How are you doing?

Is there an application to edit the text files in batch?
or do I need to do it through the terminal?  If I need to do it over the terminal, what is the proper command line?


i hope this makes sense..thanks in advance

---

### Post by _sluimers_ on 2009-07-23
Are you looking for [AWK]("http://en.wikipedia.org/wiki/AWK") perhaps?

Try finding a good tutorial about it. Google gives me [this]("http://www.vectorsite.net/tsawk.html") and [ this ]("http://www.think-lamp.com/2008/10/awk-a-boon-for-cli-enthusiasts/.").

---

### Post by McNils on 2009-07-23
[Sed]("http://en.wikipedia.org/wiki/Sed") is an alternative to awk. For some tasks sed is better to use than awk.

For your example.
for f in allmyfiles
do
 sed 's/Hello! How are you?/hello! How are you doing?/' $f > ${f}_new
done

---

### Post by bacil on 2009-07-23
it depends on edit you want to do ? is it always the same string you replacing or is it different in each file ? etc

---

### Post by 007casper on 2009-07-23
Thank you for setting me in the right path.  I also checked out synaptic. There is gawk, and mawk, and other forms of sed.

It is the same string in different parts of the file.  In some of them, it is in the begining, and in others in the middle, and sometimes at the end.  It has to match case, it is case sensitive.  Because there is the word "Hello", and "hello".  These two case sensitive words represent different files.

I have over two hundred folders, with some of them containing subfolder, and each folder containing minimum of five different text files.  

It would be ideal for the command to go through all the folders and replace the words in those text files.  Almost majority of the files that I did manually contains the words that needs to be substituted.  If the file doesnt contain the word, then it could skip that particular text file.

---

### Post by McNils on 2009-07-23
I just thought of **krename** that I tried a couple of years ago. I found it a bit to aggressive... make sure that you have a backup.

Most commands are case sensitive  so that wont be a problem. 

This snippet finds all files that ends with txt starting from current directory
**find . -name '*txt' -type f**

To find all files you can use **find**

---

### Post by 007casper on 2009-07-24
krename seems promising.  However, it doesnt seem like I have a hang of it.  I tried several things.  It just wants to rename the file's name and move it.  However, I need to change the text/source inside the file.  I dont need to rename the file. 

krename does have 'find and replace' in the interface.  I couldnt get it to work.  I tried with expression and one without... no luck.  I am pretty sure I am doing something wrong.

I tried to launch help center.  It cant launch. It says KDEInit could not launch 'khelpcenter' could not find khelpcenter executable.  I downladed the manual.  No examples.

Back to sed.  Since I dont know much about sed check these examples as well.
[http://www.ibm.com/developerworks/linux/library/l-sed1.html](http://www.ibm.com/developerworks/linux/library/l-sed1.html)

I only need "Hello" to be changed to "Hi", and also "hello" to "hi".  The whole thing is case sensitive. And overwrite the existing file.

I tried the example
sed 's/Hello/Hi/' $f > ${f}_new

it creates the _new file... what does $f > ${f} do?

So I tried 
sed -e 's/Hello/Hi/g' init.jsp

then tried
sed -e 's/hello/hi/g' init.jsp

I realized that it only changes the first occurance instance and not globally the whole file.  There are sometimes 7 to 18 instances, where "hello" needs to be changed to "hi".

I need to really create a batch process. Because doing all these files manually increases the error rate. 

I really appreciate any input.

---

### Post by 007casper on 2009-07-24
I highly recommend regexxer.  So far so good...

---

### Post by McNils on 2009-07-25
I hope that it works out with regexxer. I want to try to explain some of your problems with sed.

Sed replaces values on each line. if you have multiple instances on one line you need to add /g. 

you have to redirect the output of sed to a new file, thats why i did $f > ${f}_new. But you did not assign a filename to f. Thats why it created _new file. 

If you need to change Hello to hello and hello to hi, you can use this expression

Here is an example
```
echo Hello Hello | sed -e 's/Hello/hello/g' -e 's/hello/hi/g' 

```

---

### Post by SenHu on 2009-08-19
Very nice suggestions so far.

Here is an alternate approach using a script. It may provide more accuracy of editing and more control.

Let's say all your files are in /somedirectory and they are named *.txt. The original string is "Hello! How are you?", you want to replace it with "hello! How are you doing?".


```
# Script hello.txt
# Collect the list of files.
var str list ; lf -rn "*.txt" "/somedirectory" > $list
# Process files one by one.
while ($list <> "")
do
    # Get the next file from the list.
    var str file ; lex "1" $list > $file
    # Read file into a str variable.
    var str content ; cat $file > $content
    # Replace string
    sal -c "^Hello! How are you?^" "hello! How are you doing?" $content > null
    # Write modified content back to file.
    echo $content > { echo $file }
done
```


The script is in biterscripting language. The techniques used is called the [COLOR="Red"]File Directory Loop[/COLOR]. It is explained in the tutorial at [http://www.biterscripting.com/LearningScripting/Lesson4.html](http://www.biterscripting.com/LearningScripting/Lesson4.html) .

We are not using [COLOR="Red"]regular expressions[/COLOR] becuase the strings here do not require it. But, using the -r option for the editor commands, you can use regular expressions. See the help page for regular expressions at [http://www.biterscripting.com/helppages/RE.html](http://www.biterscripting.com/helppages/RE.html) .

Sen

---

### Post by pricinosus on 2010-09-27
How to replace Question Mark ?

When I search for  a string begining with ? (question Mark) I get this message from Regexxer:

Error in regular expression at &#8220;?&#8221; (index 1):
nothing to repeat

[IMG]http://img825.imageshack.us/img825/6705/regexxer.png[/IMG]

---

