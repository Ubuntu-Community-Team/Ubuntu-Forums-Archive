---
title: "How do I give two Client users permission to access their file system?"
date: 2011-05-01
forum: General Help
---

### Post by Cotopaxi on 2011-05-01
Hi all

The desktop computer of my two children has a total of three users:

1) The superuser (me)
2) The user 1001 (my elder son)
3) The user 1002 (my younger son)

Both users 1001 and 1002 can not access their files system, and also they can not save any attachments from incoming mails.

What I tried so far:
I accessed the file manager as superuser, and went: >Root>Home. Here I right-clicked on the folder “User 1001”, selected properties, selected the tab 'permissions' and allowed this user to read and write into this folder. I also checked the checkbox “extend this permission to all subfolders and its contents”.

The problem is, when I reboot, everything is 'forgotten' and I am at quadrant zero again.

Eventually I should state that part of the folders are from a backup drive, because the hard disk had to be replaced so, once I re-installed the OS on the new hard drive, I copied the folders from the backup drive into the home folder.

One last question:
Is there a good tutorial about permissions?

Thanks for your help!

---

### Post by Cotopaxi on 2011-05-01
Sorry, can anyone help me?

Thanks!

---

### Post by An Sanct on 2011-05-01
Which version of Ubuntu are you using?

Is this a Live CD/USB maybe?

---

### Post by idoitprone on 2011-05-01
There is a rule about bumping a thread until it is a day old.

```
ls -l /home
```


```
cat /etc/passwd
```

i am asking because i want to know who is the owner of the home directory and what are the user names.

You may soon have to use chown command to change the group and owner of the directory

---

### Post by Cotopaxi on 2011-05-01
An Sanct,
I am using version 10.10, installed on a clean hard disk.

Idoitprone,
First of all I apologize for using bump so early, I did not know that rule! Thanks for telling!

I will now change to the computer of my children and give you the output from there.

To both of you thanks very much indeed!

---

### Post by collisionystm on 2011-05-01
> **Cotopaxi said:**
> Sorry, can anyone help me?

Thanks!


You can Make 2 groups.

Group 1 = oldersonsname
Group2 = youngersonsname
Open terminal
```

groupadd nameofgroup
chgrp -R firstgroup /home/nameoffirstson
chgrp -R 2nd /home/nameofsecondgroup
chmod -R 770 /home/first
chmod -R 770 /home/2nd
usermod -G firstgroup- a firstson
usermod -G 2ndgroup -a 2ndson

```

Or just 
 
Make them the owner of their own home directory with

```

chown -R firstsonname /home/firstson
chmod -R 700 /home/firstson

```

Same for second son.

---

### Post by Cotopaxi on 2011-05-01
Idoitprone:

The first output for "ls -l /home" is:

> systemverwaltung@systemverwaltung-System-Product-Name:~$ ls -l /home
total 28
drwsrwsr-x 59 Erik             Erik              4096 2011-05-01 16:00 Erik
drwx------  2 root             root             16384 2010-12-30 16:07 lost+found
drwxrwxr-x 42 Nicolas          Nicolas           4096 2011-05-01 19:12 Nicolas
drwxr-xr-x 42 systemverwaltung systemverwaltung  4096 2011-05-01 20:05 systemverwaltung
systemverwaltung@systemverwaltung-System-Product-Name:~$ 


I will post the output of your second request in another reply, thanks so far!

---

### Post by Cotopaxi on 2011-05-01
Idoitprone,

I can't post the output of your second request, because the forum is telling me that I post 37 images in my post! It is actually quite a large output, but there are no images in there! I only copied and pasted the output from the terminal.

Please tell me, what text exactly I should post.

Thanks again!

---

### Post by Cotopaxi on 2011-05-01
Collisionystm,

Thanks for your reply,

The two users and groups are created, as can be seen in the first terminal output, which I managed to post.

Eventually I will just make them the owners of their folders, as you recommend.

Thanks!

---

### Post by idoitprone on 2011-05-01
> **Cotopaxi said:**
> Idoitprone,

I can't post the output of your second request, because the forum is telling me that I post 37 images in my post! It is actually quite a large output, but there are no images in there! I only copied and pasted the output from the terminal.

Please tell me, what text exactly I should post.

Thanks again!

what? you run in a terminal and post the output. You dont really need a picture, since you can copy and paste to this website nevermind that.

collisionystm proposed all the options you need. Since I believe this is a basic user account on a default ubuntu install, then try his second option. What I am trying to obtain is the username in /etc/password it should have a 1001 or 1002 near it as you mention in the first post. Use that username to replace the command collisionytm has mention 

pretend the user is hungryman and the home folder name is Nicolas
One more thing. Be careful with terminal commands with a capital letter option. The author dont want you to accidently type that option since it can ultimately comprise your system
```
chown -R hungryman /home/Nicolas

``` I dont think you need the second command since you all the proper permissions

---

### Post by An Sanct on 2011-05-02
Cotopaxi: 

Hint, to copy and paste in terminal use
**Ctrl + Shift + C** -> to copy selected text
**Ctrl + Shift + V** -> to paste text from the clipboard.

---

