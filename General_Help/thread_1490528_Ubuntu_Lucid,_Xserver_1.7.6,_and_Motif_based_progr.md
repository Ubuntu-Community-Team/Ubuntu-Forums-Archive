---
title: "Ubuntu Lucid, Xserver 1.7.6, and Motif based programs"
date: 2010-05-22
forum: General Help
---

### Post by PerryBothron on 2010-05-22
Hello Everyone,
Long time reader, first time poster!

I recently upgraded to Lucid, and since have been encountering an interesting bug (I think).
Applications which use some form of Motif have the problem that right clicking in a window causes the mouse to get stuck in the window and the only way to get control back is to kill the application via the console.  Normally, a pop up menu would appear.

Now, this does seems primarily happen when running said applications remotely (ie. X forwarding across an ssh connection).  I've encountered this problem in both the GRACE plotting package, and the TotalView graphical debugger, both of which use Motif in some capacity.

I've already been in discussion with the folks at TotalView about this  issue, and a bit more information can be found there: 
[http://forum.totalviewtech.com/gforum.cgi?post=707](http://forum.totalviewtech.com/gforum.cgi?post=707)
A couple of users there are able to reproduce my problem.

Searching the internet, I also found this in the RedHat bugzilla:
[https://bugzilla.redhat.com/show_bug.cgi?id=543647](https://bugzilla.redhat.com/show_bug.cgi?id=543647)

I'm running Lucid 64-bit (Linux jon-desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux), and this problem did not occur in Intrepid or Jaunty (haven't tried Karmic).

So, I guess the question is, is there any easy way to upgrade my Xserver to the latest experimental version in an attempt fix this problem?  I'm trying to avoid building from source.  I've also checked the proposed updates and backports repositories via Synaptic and don't see any Xserver update in there.

Alternatively, does anyone have any idea how long it will take for a fix to make it into the standard Lucid upgrade repositories? 

Thanks in advance for your help!
Cheers,
Jon

---

### Post by blacOnLucid on 2010-06-02
Dear Jon,
 
As for you, old reader, new poster!

I encountered exactly the same problem since Lucid migration now, using Totalview Debugger.
I'm completely stuck by this problem now ( any right click on the main TV window will make my pointer blocked in this window with on possible action).
This bug is very annoying as right click allow to set up conditional breakpoints which is a feature that I use daily in my debugging work.

Any advice on X11 update/modif or workaround Welcomed!

Bruno.

---

### Post by PerryBothron on 2010-06-02
Hey Bruno,
Glad to know I'm not the only one!
You can still set conditional breakpoints, albeit a bit awkwardly.  First set an unconditional breakpoint, then left-click to highlight the line of code you want to change to a conditional breakpoint.  Under the action point menu, select properties and you can set your conditional breakpoints.

Here's to hoping some wise soul can help us out with a fix!
Cheers,
  Jon

---

### Post by thombos on 2010-06-10
This is indeed a bug in the X server which affects most Motif applications. It has been fixed in newer versions of the xorg-server (> 1.7.7), however Ubuntu hasn't pushed this update yet. I struggled with this problem a little while ago and made a recent blog post due to requests from collegues on how to easily fix this.
Please see my blog at:
[http://twboutnothing.blogspot.com/2010/06/details-for-ubuntu-1004-xorg-server-176.html](http://twboutnothing.blogspot.com/2010/06/details-for-ubuntu-1004-xorg-server-176.html)
[U]
Thomas

[/U]

---

