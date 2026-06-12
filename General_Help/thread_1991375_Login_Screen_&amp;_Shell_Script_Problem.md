---
title: "Login Screen &amp; Shell Script Problem"
date: 2012-05-30
forum: General Help
---

### Post by James Heller on 2012-05-30
First Problem:
My ubuntu installation crashed when I was upgrading from 11.10 to 12.04. I managed to get it fixed though but..

Right now, I am stuck with this login screen: [http://imgur.com/K6K3b](http://imgur.com/K6K3b)

How do I change it to this: [http://www.tuxtree.com/wp-content/uploads/2012/05/image31.png](http://www.tuxtree.com/wp-content/uploads/2012/05/image31.png)

I tried sudo apt-get unity --reset but it doesn't work and all sorts of x-org errors comes out upon executing the command. I can't find any settings in ubuntu that can change it. The theme only changes the wallpaper and other stuff but not the login environment.

Second Problem:
Also, I have been trying to do a shell script that displays a file permission in this format:

File name: AAA
File path: /A/B/C
Owner: XYZ
Owner's Permission Access: Able to Read, Able to Write, Unable to Execute
Group: EFG
Group's Permission Access: Able to Read, Unable to Write, Able to Execute
Others' Permission Access: Unable to Read, Unable to Write, Unable to Execute

What I've gotten so far is:

```
done=false
echo "Current directory is:"
pwd
while [ $done != true ]
do
    read -p "Please enter a filepath to check permission of the file:" input
    stat -c %a $input | awk '
    BEGIN{FS=""}
    { for(i=1;i<=1;i++) a0=$i }
    { for(i=2;i<=2;i++) a1=$i }
    { for(i=3;i<=3;i++) a2=$i }
    '
    if [ $input == exit ]
    then
    done=true
    echo "The program has been terminated!"
    else if [ $input == clear ]
    then
    clear
    echo "Current directory is:"
    pwd
    fi
    fi
done

```I am not sure how to parse the result of the for loop to an if loop. Can anyone help me fix this and make the code to be more efficient?

---

### Post by aromo on 2012-05-30
> **James Heller said:**
> Also, I have been trying to do a shell script that displays a file permission in this format:

File name: AAA
File path: /A/B/C
Owner: XYZ
Owner's Permission Access: Able to Read, Able to Write, Unable to Execute
Group: EFG
Group's Permission Access: Able to Read, Unable to Write, Able to Execute
Others' Permission Access: Unable to Read, Unable to Write, Unable to Execute

What I've gotten so far is:

```
done=false
echo "Current directory is:"
pwd
while [ $done != true ]
do
    read -p "Please enter a filepath to check permission of the file:" input
    stat -c %a $input | awk '
    BEGIN{FS=""}
    { for(i=1;i<=1;i++) a0=$i }
    { for(i=2;i<=2;i++) a1=$i }
    { for(i=3;i<=3;i++) a2=$i }
    '
    if [ $input == exit ]
    then
    done=true
    echo "The program has been terminated!"
    else if [ $input == clear ]
    then
    clear
    echo "Current directory is:"
    pwd
    fi
    fi
done

```

I am not sure how to parse the result of the for loop to an if loop. Can anyone help me fix this and make the code to be more efficient?

That's 2 question on one thread... not a good practice.

For your 2nd question I'm going to give you an idea:

```
find /A -type f -exec ls -la {} \; | awk '{ print "Permissions: " $1 "\nUser: " $3 "\nGroup: " $4 "\nFullPath: $9"}'
```

where /A is your 1st level directory (not a command switch)

---

### Post by James Heller on 2012-05-31
> **aromo said:**
> That's 2 question on one thread... not a good practice.

For your 2nd question I'm going to give you an idea:

```
find /A -type f -exec ls -la {} \; | awk '{ print "Permissions: " $1 "\nUser: " $3 "\nGroup: " $4 "\nFullPath: $9"}'
```where /A is your 1st level directory (not a command switch)
Hi there, aromo. Thanks for the input. I will try to understand the command that you have given.

My first problem, I did searches around the forum but end up it only rendered my ubuntu unbootable. I had to do a fresh install to get it fixed so, it's solved already but doesn't seemed to be quite helpful since I can't find any documentation to solve it.

---

### Post by James Heller on 2012-05-31
How can I put it in a non-tech savvy readable format like how I specified it in the first post?

The commands you gave me only show octal permissions where I want to translate it into simpler form.

---

### Post by James Heller on 2012-06-03
Help anyone?

---

