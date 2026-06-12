---
title: "root access"
date: 2012-10-02
forum: General Help
---

### Post by h66m9d on 2012-10-02
hi
I want to run my computer in root access for all my software
for example when I want run nautilus in root access must I run it from root access in terminal separate, but I need start all my software in desktop in root access without run one by one in terminal. (I have Ubuntu 12.4)

---

### Post by snowpine on 2012-10-02
Use 'sudo' for the apps you really need to run as root.

4 magic letters: sudo

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by raja.genupula on 2012-10-02
> **snowpine said:**
> Use 'sudo' for the apps you really need to run as root.

4 magic letters: sudo

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)


+1 and one more point . run GUI apps with gksudo instead of sudo

---

### Post by h66m9d on 2012-10-02
> **snowpine said:**
> Use 'sudo' for the apps you really need to run as root.

4 magic letters: sudo

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
for example I want have root access when click on "home folder" icon on my desktop without need to open terminal

---

### Post by snowpine on 2012-10-02
> **h66m9d said:**
> for example I want have root access when click on "home folder" icon on my desktop without need to open terminal

No you don't because then you'll have permission problems with files owned as root that should be owned by your user. Root access is not necessary to browse your /home folder.

---

### Post by h66m9d on 2012-10-02
> **snowpine said:**
> No you don't because then you'll have permission problems with files owned as root that should be owned by your user. Root access is not necessary to browse your /home folder.
I know. but my idea possible technically?

---

### Post by snowpine on 2012-10-02
> **h66m9d said:**
> I know. but my idea possible technically?

Yes and described in the link from post #2.

---

### Post by Lars Noodén on 2012-10-02
It will quickly make a mess of your account and eventually the whole machine.  There's a long history behind it being actively discouraged.

---

### Post by The Cog on 2012-10-02
> **h66m9d said:**
> I know. but my idea possible technically?

It is technically possible. But it is actively discouraged, to the point of being part of the forum policy not to tell you how to do it. 

In your normal working you do not need to stray outside your home folder, so you do not normally need write access there. Only when you act as system administrator do you need that write access, and that won't be very often once you have the machine configured as you like it. Having read-only access outside your home folder means you are less likely to make mistakes that trash the system, and make it more difficult for any malware you run to take over the system. It also makes you think more carefully at the times when you do adopt the higher access rights.

---

### Post by deadflowr on 2012-10-02
Setting your system to run as root is wholeheartedly possible, but absolutely unnecessary.
Note that when you run as root, everything done is done as root. Which includes moving user files. If you move a file which was owned by a user( other than root) that file becomes owned by root.
There should be only a limited need to run as root. If your programs you need, which should run without root, need root access to run, then you probably need to look at the file permissions to make sure their set right.
There are commands you can run in a terminal to grant root once, and then execute your programs as you want.
As some, either stickie, or wiki notes, if you believe your experienced enough to run as root, then you shouldn't need to ask how.

---

### Post by ezsit on 2012-10-02
**deadflowr** wrote:
> ... if you believe your (sic) experienced enough to run as root, then you shouldn't need to ask how.

Very well stated!!! The corollary would be:

**"If you believe you need to run as root all the time, then you are NOT experienced enough to run as root at all."**

---

### Post by 1clue on 2012-10-02
Just about every Linux user I know gets to a point where they want to run as root all the time.  Been there, done that.

Generally speaking, you do it once and screw your box up so badly you need to reinstall.

Then you do it again and try to be smart about it, and then take longer to screw your box up so badly you need to install.

Then you either wise up or you try again, however many times.

For me the light bulb came on when I inadvertently ran malicious code as root.

There is a Really Good Reason to run as a non-privileged user unless absolutely necessary.


**PS**

The whole 'malicious code thing:  That means I had to cancel my credit cards, warn my bank, reinstall, change all my passwords and send out emails apologizing for spewing malicious code across the net.

---

### Post by JKyleOKC on 2012-10-02
One more point that nobody seems to have brought up: If you **do** decide to run only as root, and do so, **please** unplug your machine from the Internet. I do not want your hubris and resulting badly-infected system spewing more spam and DDOS activity into the communications system that the rest of us use.

---

### Post by NadirPoint on 2012-10-02
Some other distros enable manual login as root by default.  I don't understand the irrational fear of allowing the user to indulge his desire to do whatever they want.  maybe they will learn something YOU can't teach them.  It is after all, their box to with as they please.  I find some of you holier than thou types really amusing.  Who made you the superuser police, anyway?  :p

A simple google search quickly reveals the command to enable root login.

---

### Post by 1clue on 2012-10-02
There is no irrational fear in this case.  It's hours of work and thousands of dollars drained out of my bank account due to my desire to "do what I want with my box."  It's having to wait until new credit cards and new checks show up, and a new payday to buy groceries.

I don't care who you are.  There will always be somebody who knows how to break through your security.  Running as root only makes it incredibly easier for them.

You and anyone else are of course free to do whatever you want with your box.  The command to run as root is trivial, and so is enabling root login on Ubuntu.

This site makes it a policy to not reveal that information, and even on forums for distros which allow root login by default the people who have been around will strongly advise against running as root when not necessary.

That said, if you choose to run as root and get pwned you will NOT get any sympathy.  You were warned repeatedly by people who have already been there and done that.  Sort of like warning the toddler to stay away from the steps, and they generally figure out why on their own even after all the warnings.

What you see on this thread is strong advice to NOT be stupid.  It's not direction or police action.

---

### Post by NadirPoint on 2012-10-02
> **1clue said:**
> There is no irrational fear in this case.  It's hours of work and thousands of dollars drained out of my bank account due to my desire to "do what I want with my box."  It's having to wait until new credit cards and new checks show up, and a new payday to buy groceries.
Sounds like you learned the lesson well.  Hard lessons are as they say, well learned.

---

### Post by 1clue on 2012-10-02
Yes.  And chances are every other naysayer on this thread has learned it well enough the hard way too, although hopefully not with such a huge price tag.

And before you start devising encryption in unlikely places, think "key logger."  No amount of encryption or complex password memorization covers that hole.  The oldest, simplest ones are the best evidently.

---

### Post by 1clue on 2012-10-02
Let me post another one that might sum it all up nicely.

If you run Linux pretty much out of the box and follow even basic security practices, then you can be cracked by somebody who knows how to use a search engine, is antisocial, does a lot of reading and who has a strong desire to get what you're hiding.

If you run Linux as root, you can be cracked by someone who is lazy, antisocial and who has yet to experience acne.

---

### Post by oldos2er on 2012-10-02
> **h66m9d said:**
> hi
I want to run my computer in root access for all my software
for example when I want run nautilus in root access must I run it from root access in terminal separate, but I need start all my software in desktop in root access without run one by one in terminal. (I have Ubuntu 12.4)

From the forum do's and don't's:

DON'T 12) Post how to allow root logins

You've gotten some good answers, so I'm closing the thread. Thanks for participating, everyone.

---

