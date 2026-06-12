---
title: "Automation"
date: 2010-10-13
forum: General Help
---

### Post by conradin on 2010-10-13
Hi All,
Im trying to automate a web page process of logging in, pressing a few distinct buttons and logging out. I can write a program which does this in VB, but Im wondering if there is a linux way to do this.

 Also note That macros probably wont work since layout changes regularly. (names of buttons, and coded content remains pretty constant though)


Im using 10.10, with gnome, & Firefox if that helps at all. 
Anyone have some insight?

---

### Post by lovinglinux on 2010-10-14
Did you accidentally marked the thread as solved? If yes, then undo that, otherwise people won't reply.

Try [iMacros]("https://addons.mozilla.org/en-US/firefox/addon/3863/") extension for Firefox. It is designed to do exactly what you want.

---

### Post by conradin on 2010-10-14
Darn, How do i un-mark it as solved?

---

### Post by conradin on 2010-10-14
Hi All,
Im trying to automate a web page process of logging in, pressing a few distinct buttons and logging out. I can write a program which does this in VB, but Im wondering if there is a linux way to do this.

Also note That macros probably wont work since layout changes regularly. (names of buttons, and coded content remains pretty constant though)


Im using 10.10, with gnome, & Firefox if that helps at all.
Anyone have some insight?

---

### Post by krishnandu.sarkar on 2010-10-14
What do you mean by Linux way..?? Well...there is Gambas, it's just similar to VB in linux.

---

### Post by lykwydchykyn on 2010-10-14
**curl** can probably do this, though I can't say I've attempted something like this.

Check out the curl command, or else if you prefer the curl libraries of your preferred scripting language (gambas, python, tcl, etc).

---

### Post by conradin on 2010-10-14
By The linux way, I mean not making system calls to the Microsoft windows os, and instead using linux aps to perform the same task. Having a graphical application isn't necessary to me, I just want to have a script or program to do some simple clicks for me at scheduled times on certain web-pages. 

I'll check out curl, though I'm still hopeful to gain insight form people who have done similar tasks.

---

### Post by lovinglinux on 2010-10-14
> **conradin said:**
> Darn, How do i un-mark it as solved?

Through the Thread Tools menu, on the top right of the thread.

---

### Post by lisati on 2010-10-14
Duplicate threads merged and "solved" removed

---

### Post by conradin on 2010-10-14
WOW curl is neat!
curl --user name : password  [http://www.somesite.com](http://www.somesite.com)

That bit works fine, I login and it drops the entire page main page.
I enter my user name where it says "name" and password next to the place where it says password, but it still requires I press enter. How can I tell this line of code to just proceed with no input, or press enter on its own or some thing? 
(I want this to turn into a scheduled task, which wont run very well if it needs user input)

---

### Post by conradin on 2010-10-15
I could use some help with my current issue:
When the curl command loads the password, it prompts for the [ENTER]
button press. How ever I would like this to be fully automatic, otherwise I need to hit enter, and the entire purpose is gone. 

I tried putting /n before and after the password to get CRLF but it hasn't worked. Does anyone who how to get this done?

---

### Post by lykwydchykyn on 2010-10-16
I believe you want to look at the "expect" command. or perhaps you can do something like this:
```

curl --user name http://someurl <<EOF
password
EOF

```

---

### Post by conradin on 2010-10-21
Thanks for the code advice but it doesn't seem to work, just requires I hit [ENTER] before it continues. I tried EOL too. 

As for the expect scripting, I read the man pages and some other articles over the past few days, and I still have no idea how to use it. It would seem like expect is the way to go though. Can anyone point me to a good tutorial for a newb to expect? 


> **lykwydchykyn said:**
> I believe you want to look at the "expect" command. or perhaps you can do something like this:
```

curl --user name http://someurl <<EOF
password
EOF

```

---

