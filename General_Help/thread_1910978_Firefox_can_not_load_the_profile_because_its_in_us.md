---
title: "Firefox can not load the profile because its in use"
date: 2012-01-18
forum: General Help
---

### Post by Dyzaster on 2012-01-18
So i keep having the below error pop up.

[IMG]http://i1103.photobucket.com/albums/g469/TheDyzaster/Forums/Screenshot.jpg[/IMG]

I have Googled this yet ive found no answer on how it can be fixed. I tried killing Firefox, and i tried rebooting my computer and selecting the profile the first time i start Firefox. Still it doesnt work, and i have seen nothing else to help me. I can choose the Default profile but i need to get this profile running.

Anyone know how to fix this?

Thank you

  -The Dyzaster

---

### Post by xyzzyman on 2012-01-18
First result from a google search for 'firefox profile in use':

[http://kb.mozillazine.org/Profile_in_use](http://kb.mozillazine.org/Profile_in_use)

---

### Post by lechien73 on 2012-01-18
Hello and welcome to the forums,

It could be because Firefox has not deleted the **lock** file that it creates in the profile folder.

So, you could try the following:

Open a terminal window and type:

```
cd .mozilla/firefox
ls
```

Now type change to the profile directory you want to look at - it may be called JohnDoFox.default, or something like that. If you don't see any directories of that name, then:

```
cat profiles.ini
```

Which will give you the directory, which corresponds to each profile.

When in the profile directory, check for the existence of a file named **lock**. If it's there, just delete it with:

```
rm lock
```

Please let us know how you get on :)

---

### Post by Dyzaster on 2012-01-18
> **xyzzyman said:**
> First result from a google search for 'firefox profile in use':

[http://kb.mozillazine.org/Profile_in_use](http://kb.mozillazine.org/Profile_in_use)


Re-Read my post.

I Googled, found that exact topic, and followed its instructions. 
Didnt help.

---

### Post by Dyzaster on 2012-01-18
> **lechien73 said:**
> Hello and welcome to the forums,

It could be because Firefox has not deleted the **lock** file that it creates in the profile folder.

So, you could try the following:

Open a terminal window and type:

```
cd .mozilla/firefox
ls
```Now type change to the profile directory you want to look at - it may be called JohnDoFox.default, or something like that. If you don't see any directories of that name, then:

```
cat profiles.ini
```Which will give you the directory, which corresponds to each profile.

When in the profile directory, check for the existence of a file named **lock**. If it's there, just delete it with:

```
rm lock
```Please let us know how you get on :)

When i did cat profiles.ini this is what came up:

[General]
StartWithLastProfile=0

[Profile0]
Name=default
IsRelative=1
Path=eg32sumr.default


[Profile1]
Name=JonDoFox
IsRelative=1
Path=profile
Default=1



rm lock was unsuccessful even while using sudo. 

Thanks for the help :)


P.S. I have Ubuntu 10.04 and i upgraded Firefox (Thinking it would fix the problem) But it didnt change anything.

---

### Post by lechien73 on 2012-01-18
Hmmm...that's strange. If you type:

```
cd ~/.mozilla/firefox/profile
ls

```
Does the **lock** file exist?

Perhaps what you could do is try:

```
cd ~/.mozilla/firefox/profile
mkdir ../newprofile
sudo cp -r * ../newprofile
cd ../newprofile
sudo rm lock
```

Now change the path in profiles.ini

```
gksudo gedit ../profiles.ini
```

Change the path for JohnDoFox to *newprofile*, save and close.

Try Firefox again :)

---

### Post by Dyzaster on 2012-01-18
> **lechien73 said:**
> Hmmm...that's strange. If you type:

```
cd ~/.mozilla/firefox/profile
ls

```Does the **lock** file exist?

Perhaps what you could do is try:

```
cd ~/.mozilla/firefox/profile
mkdir ../newprofile
sudo cp -r * ../newprofile
cd ../newprofile
sudo rm lock
```Now change the path in profiles.ini

```
gksudo gedit ../profiles.ini
```Change the path for JohnDoFox to *newprofile*, save and close.

Try Firefox again :)

When i ran sudo rm lock the same thing happened:
rm: cannot remove `lock': No such file or directory

But im about to restart Firefox and see if this worked :D

---

### Post by Dyzaster on 2012-01-18
Yes! It worked :D Thank you very much for your help!


If you dont already use it check out JonDoFox, its a very good VPN/Proxy i use :D I just recently re-installed Ubuntu 10.04 and never had this error before, thats why i was having trouble lol.

Thanks again :)

  -The Dyzaster

---

### Post by Dyzaster on 2012-01-18
I ran into a problem.

This problem actually answered the question as to why i was having problems in the the first place.

The reason i couldnt load the profile was because of the permissions the "profile" folder had. Its completely locked down and its not supposed to be.

Now i just have to find out the permissions for "eg32sumr.default" Which is the default profile for Firefox, and then i have to transfer the permissions over to "profile" to see if that works :D


Heres the privileges of the folder that i need to transfer to "profile"

drwx------ 11 dyzaster dyzaster 12288 2012-01-18 09:34 eg32sumr.default

Heres the privileges of "profile"

drwxrwxrwx 11 root root 12288 2012-01-18 09:26 newprofile


It looks like all i have to do is change root root to dyzaster dyzaster

sudo chmod -R --reference="eg32sumr.default" "newprofile"



EDIT: i had to do chown -R dyzaster:dyzaster  to both "profile" and "newprofile" and now they both work correctly!





If anyone has this problem the way to fix it from the beginning is to enter:

sudo chmod -R --reference=eg32sumr.default "newprofile"

This gives the permissions of the NEW profile (change "newprofile" to the name of the profile itself with/without quotes) the same permissions of the default directory and that will fix the problem.

---

### Post by lechien73 on 2012-01-18
Excellent...could you mark the issue as [SOLVED] using the **Thread Tools** menu at the top of the page when you get chance?

Glad it's working for you now :D

---

### Post by lovinglinux on 2012-01-20
> **Dyzaster said:**
> I ran into a problem.

This problem actually answered the question as to why i was having problems in the the first place.

The reason i couldnt load the profile was because of the permissions the "profile" folder had. Its completely locked down and its not supposed to be.

Now i just have to find out the permissions for "eg32sumr.default" Which is the default profile for Firefox, and then i have to transfer the permissions over to "profile" to see if that works :D


Heres the privileges of the folder that i need to transfer to "profile"

drwx------ 11 dyzaster dyzaster 12288 2012-01-18 09:34 eg32sumr.default

Heres the privileges of "profile"

drwxrwxrwx 11 root root 12288 2012-01-18 09:26 newprofile


It looks like all i have to do is change root root to dyzaster dyzaster

sudo chmod -R --reference="eg32sumr.default" "newprofile"



EDIT: i had to do chown -R dyzaster:dyzaster  to both "profile" and "newprofile" and now they both work correctly!





If anyone has this problem the way to fix it from the beginning is to enter:

sudo chmod -R --reference=eg32sumr.default "newprofile"

This gives the permissions of the NEW profile (change "newprofile" to the name of the profile itself with/without quotes) the same permissions of the default directory and that will fix the problem.


Never run Firefox with *sudo* and you won't face that problem again.

---

