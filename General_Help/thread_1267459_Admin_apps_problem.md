---
title: "Admin apps problem"
date: 2009-09-15
forum: General Help
---

### Post by HarrisonNapper on 2009-09-15
I have implemented the rather simple work-around for this issue of running everything from the terminal with sudo; however, I had a system crash (long story) and now every time I log in, a crash report pops up on my taskbar. That wouldn't be an issue except that since I can't launch it, it pops up every time I log in. Also, I would like to be able to test out the GUI on ubuntu and see how it works :-P

So, now that I've covered the nature of the problem, here are the symptoms:

When I launch an admin app from the admin menu, it will open the "Starting Administrative Application" window and then close. I have literally copied and pasted the path from the launcher properties into the terminal and the exact same command works. Sometimes. At other times (like just now) I get the following error:
> 
Lock taken by pid: -1. Exiting.
What little information is out there on this tells me that in gksu it works something like
> 
  if (pid != 0)
    {
      g_warning ("Lock taken by pid: %i. Exiting.", pid);
      exit (0);
    }
(that's from libgksu source) and I have seen other errors reported on older versions of gksu than I have and on different pids than -1.

Furthermore, when I try to run synaptic by typing "synaptic" I get the error "Starting without administrative privileges"; my understanding is that this is common and synaptic should be run with gksu. Finally, let me say in advance that I have added myself to the admin and root groups, deleted the .cache file in my home directory in case it was an issue with stored authentication.

I know that might be tl;dr for a lot of you, I just wanted to make sure I got as much of the basic info out there as possible. Any help would be very much appreciated and thank you all in advance for volunteering your time like you do; it's part of what makes the Ubuntu community a community. For serious.

Some info about my setup:
Dell Studio XPS 1340
Ubuntu Studio Jaunty amd64

---

### Post by HarrisonNapper on 2009-09-16
bump

---

