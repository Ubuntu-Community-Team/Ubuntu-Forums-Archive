---
title: "Hi, I'm new to Ubuntu, and having problems installing bluesnarf"
date: 2010-01-05
forum: General Help
---

### Post by kash11100 on 2010-01-05
I did a search on this site for bluesnarf in the search box @ the top right, but didn't see any results, so hopefully I'm not the 100th person to ask this, but:

I'm trying to install bluesnarf. I was following the instructions on this guys site([http://taufanlubis.wordpress.com/2008/09/14/how-to-install-bluesnarfer-in-linux-ubuntu/](http://taufanlubis.wordpress.com/2008/09/14/how-to-install-bluesnarfer-in-linux-ubuntu/)), and from the bluez-4.59 folder, issued the command "./configure ; make ; make install"(before that i issued "su root")...up until that command, all was fine, however, when I issued it, a long list of text displays on the screen, ending with:
Configure Error: D-Bus Library is required
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
---------
I figured I'd deal with one issue at a time, so I tried to install D-Bus, first by doing it from the Ubuntu Software Center (I downloaded a gmail app that I wanted anyway, and it supposedly came with and installed "D-Bus")...but still it produced the same error, saying "D-Bus library is required"...

So I found another webpage about installing D-bus ([http://www.linuxfromscratch.org/blfs/view/cvs/general/dbus.html](http://www.linuxfromscratch.org/blfs/view/cvs/general/dbus.html)), which said to use the following commands as a root user: 
groupadd -g 18 messagebus &&
useradd -c "D-BUS Message Daemon User" -d /dev/null \

(I figured I could do this from any directory, so I tried it from whatever
directory I was in at the time, I apologize but I don't remember which).
Anyway, I just tried to recreate the error for this posting, but this 
time when I typed all of the above on one line a ">" came up. Previously,
I could have sworn that didn't come up, and it just said "Group Messagebus already exists". 
This time, when the ">" came up, I just hit enter, and it said the same 
thing, about the group already existing. I went to "System/Administration
/Users and Groups, and saw that it was indeed there, but there was no
user called D-Bus as the page I was reading said there should be, and
I couldn't find a way to add one.

I figured I'd just try and see if skipping that command and executing the
next one listed on the page would somehow make it work anyway...(wishful thinking, I know!)
So I issued:
./configure --enable-tests --enable-asserts &&
make &&
make check &&
and this complained about a expat.h file not being around. I have some experience with C, so
I knew it was a header file, and I placed the file in a D-Bus directory I made under the BlueSnarf
dir...to no avail. Then I looked at the Error file it generated, and realized it was looking
for it in the USR/BIN/LD directory, which apparently doesn't exist on my comp.
The file that told me this was config.log...
Anyway, I'm pretty new to Ubuntu, but I'm trying to learn the ropes, so any help would be greatly appreciated, perhaps if
I can learn to install this program, then I won't be so intimidated to install stuff from outside the nice little GUI Software Center
in Ubuntu that does all the hard work for me!

Thanks for taking the time to read this,

--kris

---

### Post by gordintoronto on 2010-01-05
From Wikipedia:
"Bluesnarfing is the unauthorized access of information from a wireless device through a Bluetooth connection...
"Because Bluesnarfing is an invasion of privacy, it is illegal in many countries."

I'm not surprised you're not getting help on this.

---

### Post by kash11100 on 2010-01-05
Honestly, I just wanted to freak my parents out, because my mom has a cell with bluetooth and I wanted to show her what I could do...lol. But, I can understand everyone's reluctance to help, so it's no biggie. Thanks for the post anyway. :)

---

