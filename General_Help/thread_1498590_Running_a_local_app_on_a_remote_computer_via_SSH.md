---
title: "Running a local app on a remote computer via SSH"
date: 2010-06-01
forum: General Help
---

### Post by Citizen Bleys on 2010-06-01
I'm not really sure how to explain this generally, so I'm going to have to paint a specific scenario.

I'm starting to learn programming in Ruby.  I have a lot of intermittent periods of spare time at work, where I have to use a Windows machine.  Now, at home, if I want to edit a .rb file, I SSH in via nautilus and use gedit.  At work, I can't do this without using nxclient, which is unacceptably laggy.  I have Portable PuTTY, so I can use command-line SSH, but in a chrooted environment with a very primitive, uncustomized (and from my attempts to write a .vimrc, uncustomizeable!) version of vi.  There's no nano and no pico.  In the web host's version of vi, neither the arrow keys nor backspace work--they just type random, capital letters.

I'm thinking that since I can use my local gedit when connecting via nautilus SSH, surely it's possible to SSH into my Ubuntu box, then SSH from there into the web host, and call *my* vi instead of the host's.  When I run vi at home, it works perfectly.  Does anyone know how to do this?  Since it's all command-line, having the 2 SSH connections shouldn't produce any noticeable lag, unlike using a graphical environment via nx.

I'm not sure if it's relevant, but I'm running Lucid, and the host is running CentOS.

---

### Post by sdennie on 2010-06-01
If you've mounted things via nautilus, they likely will be available on the commandline in ~/.gvfs.  In which case, you can edit files using your local copy of vim.

---

### Post by chessnerd on 2010-06-01
So you are using Computer A locally, and you want to run a an app on Computer B that is actually running on Computer A?

---

### Post by Citizen Bleys on 2010-06-01
> **sdennie said:**
> If you've mounted things via nautilus, they likely will be available on the commandline in ~/.gvfs.  In which case, you can edit files using your local copy of vim.

That's no good -- I'd have to mount it from the GUI, and SSH via Nautilus times out after about 5 minutes without disk activity on my host; it takes me 90 minutes to get from home to work.  Although if both computers were mine I could just eliminate the timeout and that would be fine :)

> **chessnerd said:**
> So you are using Computer A locally, and you want to run a an app on Computer B that is actually running on Computer A?

Correct.  The issue is that both computers have vi installed and I want to be able to call *my* vi, not the server's, while SSH'd into the server.

I'm going to try to use sshfs to mount my directory on the server locally and then just SSH into my own computer and use vi from there, but I won't know if that will work until I actually try it remotely.  I'm not sure what kind of timeout is in place via command-line SSH.

---

