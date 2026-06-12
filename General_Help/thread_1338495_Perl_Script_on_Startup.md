---
title: "Perl Script on Startup"
date: 2009-11-26
forum: General Help
---

### Post by Rhiknow on 2009-11-26
Greetings,

I want to run the following script on startup:

sudo perl /home/rhiknow/.cpan/build/Stardust-0.07/bin/stardust.pl --port=5742 --base=/comet

It must be run by sudo.

I don't want to have to keep a command line window open all the time so as to be able to interact with my stardust server.

Can anyone point me in the right direction? I've put a script called 'stardust' in /etc/init.d containing the following line:

perl /home/prestocab/.cpan/build/Stardust-0.07/bin/stardust.pl --port=5742 --base=/comet

But when I run this on the command line, i.e.:
> sudo /etc/init.d/stardust 
I get the following error:

"Bareword found where operator expected at /etc/init.d/stardust line 3, near "--port"
	(Missing operator before port?)
Bareword found where operator expected at /etc/init.d/stardust line 3, near "--base"
	(Missing operator before base?)
syntax error at /etc/init.d/stardust line 3, near "/."
Search pattern not terminated at /etc/init.d/stardust line 3."

Could someone please point me in the right direction?

Many thanks in advance,

---

### Post by raktarok on 2009-11-26
You can remove the sudo and add the line in the file /etc/rc.local. The file is read during boot time and it is there for purposes like this, I think. 
This should work, but if it does not, then you will have to add the line in your startup applications list, and then tinker with the file /etc/sudoers, so that your command runs without requiring a password.

---

### Post by Rhiknow on 2009-11-26
Legend! That did the trick. Thanks for your reply.

I just added the line
perl /home/prestocab/.cpan/build/Stardust-0.07/bin/stardust.pl --port=5742 --base=/comet &
to my /etc/rc.local (before the line "exit 0")

---

### Post by raktarok on 2009-11-26
Good to hear that!

---

