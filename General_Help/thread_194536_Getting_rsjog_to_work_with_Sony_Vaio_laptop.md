---
title: "Getting rsjog to work with Sony Vaio laptop"
date: 2006-06-11
forum: General Help
---

### Post by eeefresh on 2006-06-11
Cross-posted on hardware forum...

I am trying to get the jog dial on my Sony Vaio PCG-GR300 laptop to work with Dapper. When I searched the forums, I discovered rsjog, which looks like a cool program.  I downloaded it from the repositories, but I am not sure how to use/activate it (I'm new to Linux, so please be kind!)

It's installed, but where do I find it? Just turning the jog dial doesn't seem to do anything, so I am assuming I have to activate it somehow. Can anyone help?

---

### Post by eeefresh on 2006-07-31
Okay, I found some instructions in the Install file, but I don't quite understand how to configure everything.  The FN keys are working, but the jogdial still doesn't do anything.  Can anyone help?  It looks like sucha cool utility, I just can't get it to work right...

---

### Post by ranf on 2006-07-31
There is some stuff in
/usr/share/doc/rsjog/

Basically you copy the 2 sample.* files to your home directory and rename them to ".rsjogrc" and ".rsjog.menu".

---

### Post by eeefresh on 2006-07-31
Thanks for the response.  I did copy the sample files into the home drectory, and the FN keys seem to be working, though I need to reconfigure them.  They seem to be off by one key.  For example, if I want to mute my laptop, I have to push the button next to the actual PC mute button.

I also still can't get get the jog dial to do anything.  Am I missing something?

---

### Post by eeefresh on 2006-07-31
Sorry to be so vague.  Maybe I can get more specific.

Here is what I see in the install file(in bold):

[B]You'll need:
  ruby
  libgtk-ruby
  xlibs-dev (the X11 library headers)
  The X11 XTest extension (don't worry, you should have it built in)
  spicctrl (to change the brightenss of your lcd screen)
  aumix (to change the volume)[/B]

I believe I have all these since I downloaded through Synaptic.

[B]Then just:
  make
  su -c "make install"[/B]

I don't understand this.  When I paste it into terminal, I get this:

[I]doug@doug-laptop:~$   su -c "make install"
Password:
su: Authentication failure
Sorry.[/I]

[B]And copy the sample .rsjogrc and .rsjog.menu to your home directory and
tweak.[/B]
Did this, but as I said, I am having trouble figuring how to tweak.

[B]Run rsjog from your .xsession like this:
  rsjog &[/B]

Not sure what this means at all.  How do I run from .xsession?  What is it?

Thanks in advance for the help.  I am a Linux/Ubuntu newbie, but I appreciate the support!

---

### Post by eeefresh on 2006-08-01
Anyone?

---

