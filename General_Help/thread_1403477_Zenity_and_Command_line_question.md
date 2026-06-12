---
title: "Zenity and Command line question"
date: 2010-02-10
forum: General Help
---

### Post by asensio on 2010-02-10
I'm coding a script in bash an zenity.

When I run the script in the shell, there's a command that waits for a response [y/N]

I'm trying to use the zenity --question dialog box

How can "connect" my response in the cli to Zenity, so when I click "YES" in the question box, the command recognizes it and runs normally?

Cheers and thank you

---

### Post by chewearn on 2010-02-10
Example:

```
zenity --question --title='Question' --text='What?'
if [ $? -eq 0 ] ; then
    echo Ok
else
    echo Cancel
fi

```

---

### Post by sisco311 on 2010-02-10
```
zenity --question && yes y | command || yes N | command
```

---

### Post by asensio on 2010-02-10
Thank you both
It's rocking :guitar:

---

### Post by asensio on 2010-02-10
Oh man... I was wrong. Well, let me tell you exacting what I'm trying.

I'm using Zenity as a GUI to **jadmaker**

I'm using this code (the part that i have doubts is in [COLOR="Red"]red[/COLOR]):

```
#!/bin/sh

FILE=$(zenity --file-selection --title="Select a JAR file")
echo $FILE
case $? in
0)
zenity --question && yes y | [COLOR="Red"]jadmaker "$FILE" ; zenity --info --text="JAR file created"[/COLOR] || yes N | zenity --info --text="Canceled";;
1)
echo "No file selected.";;
-1)
echo "No file selected.";;
esac
```

the jadmaker man page is tiny:

> jadmaker [-f|--force] [-u|--url URL] <filename.jar>... 

-h, --help
    Show summary of options. 
-f, --force
    Force rewriting of JAD file even if exists. 
-u, --url URL
    Define URL to be included in JAD file.

When jadmaker "$FILE" is called, if the files exists, the terminal waits for a response: overwrite? [y/N] 

This seems to be so simple, what am I doing wrong?
Thank you for taking some of your time to help a noob

---

### Post by flippo on 2010-02-10
So, your saying that your problem is that jadmaker is pausing on the terminal with a Y/n prompt?

If so, can't you just ask the question beforehand then run jadmaker with the --force option to get past the prompt, only if you get a response that tells you to?

---

### Post by asensio on 2010-02-10
Thanks for your reply flippo,

I could do that, but then I would have to test if the file already exists. That seems tricky...

After selecting the jar file (let's say something.jar) I have to test if there is a file named "something.jad"

maybe it's better I keep it simple and always use the forçe :biggrin:

cheers

---

