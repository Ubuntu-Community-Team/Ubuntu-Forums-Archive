---
title: "Lost permission to my home directory (somehow)"
date: 2010-07-14
forum: General Help
---

### Post by szczecinmeister on 2010-07-14
Hi,

I just recently installed a netbook version of lucid. Since it didn't support wifi, I did a wget of the 2.6.35 kernel and since then the netbook has been working great WITH wifi. It has been functioning great so far.

Yesterday I went to add a user account for my girlfriend and that's when things went haywire.

There were a number of error messages when I tried to log into both her account and mine after creating it:
First error: Could not update ICEauthority file /home/bob/.ICEauthority
Second error: There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)
Third error: Nautilus could not create the following required folders: /home/bob/Destop, /home/bob/.nautilus

I have inspected the /home drive and made sure I have permissions for my /home/bob dir, but it doesn't seem to allow me to cd bob. The current permissions for user is drw-rw-r-- and it is owned by bob.

Thanks in advance!
-Alex

---

### Post by sisco311 on 2010-07-14
Hi and welcome to the forums!

You need execute permission for the directory in order to be able to cd into it. Switch to a virtual console (Ctrl+Alt+F2), log in and set the permissions:
```
chmod 0755 /home/bob
```
or for a private home:
```
chmod 0700 /home/bob
```

[noparse]Press Ctrl+Alt+F7 (or F8) to switch back to the login screen.[/noparse]

---

### Post by QLee on 2010-07-14
szczecinmeister,

I'm confused by your question, you show us errors from a home folder from "alex" then you ask about getting into a home folder for user "bob".

The error you show seems to point to a possible problem with the "alex" folder, did you let the system create it as part of the add user process or some other way.

---

### Post by Braik on 2010-07-14
Hi there,
 
to QLee: I think that szczecinmeister is trying to explain us the problems he is facing and Alex is his girlfriend and Bob is himself. :D
 
to szczecinmeister: I had a similar problem when I re-installed a system, and because my home folder is on another harddrive I did not mounted to /home carefully. I don't remember exactly what I did but I just remember that it was a problem of premissions so I think that sisco311 solution should be good for your home issue.
 
For the issue of your girlfriend username I sugest that once your rights are correctly set just delete (don't forget to delete her home folder) and create again her acount.

---

### Post by jayanramesh on 2010-07-14
Dear Sisco311,
I had the same problem and  I did the way you have shown above but it gave me the error as "missing operand after '0755 /home/jayan'.Could you guide me to rectify this .
Thank you

---

### Post by QLee on 2010-07-14
[QUOTE=Braik]to QLee: I think that szczecinmeister is trying to explain us the problems he is facing and Alex is his girlfriend and Bob is himself. :D
 [/QUOTE]

<chuckle>

---

### Post by sisco311 on 2010-07-14
> **jayanramesh said:**
> Dear Sisco311,
I had the same problem and  I did the way you have shown above but it gave me the error as "missing operand after '0755 /home/jayan'.Could you guide me to rectify this .
Thank you

Type a space between the octal permissions (0755) and the path to the home directory (/home/jayan).

```
chmod 0755 /home/jayan
```

---

### Post by jayanramesh on 2010-07-14
Dear Sisco311,
Thank you so much ,I will try.

---

### Post by szczecinmeister on 2010-07-14
QLee & Braik: It happens in both so I've just changed it to bob, sorry for the confusion!

sisco311: you're a legend! I was using the wrong permissions... I was using 0655 and 0600 instead of 0755 and 0700 :-# thanks for your prompt response I really appreciate it :) and thanks for the great welcome to the forums!

---

### Post by sisco311 on 2010-07-14
You're welcome!


Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

Thanks.

---

### Post by Braik on 2010-07-16
Hi sisco311,

I just added a user for my girlfriend too, but when she tries to log on all the messages of szczecinmeister appears, my acount is ok, no prob but I am unable to repair my girlfriend account.

I have tried to delete user (and all files) and recreate everything but nothing good.

I have tried to log in in console mode but nothing. all the commands you give in this topic and still nothing

Please help me

---

### Post by sisco311 on 2010-07-16
Hi Braik, 

Try to create the new user from the cli:
```
sudo adduser **username**
```

If that doesn't work, then please post the output of:
```
sudo ls -al /home/**username**
```
where **username** is the name of the new user.

---

### Post by Braik on 2010-07-17
Sorry about the panic, but I found the solution myself ;).

This happened because of my config. My /home folder is in fact a supplementary hard drive, like that I can re-install or upgrade without any fear about crashing my data. But because of that I forgot to give the permissions to any other user, and I was the only one to have access to...

I have just right-clicked on the folder and tell him that users have any access to it.

Thanks anyway

Bye

---

