---
title: "Assign application to a specific CPU core"
date: 2010-05-07
forum: General Help
---

### Post by nedmar on 2010-05-07
Hi,

I try to make 2 applications ( firefox and wine ) to work each one using a different core of my dual core CPU (e.g. i wanna firefox to use CPU0 and wine to use CPU1). In windows this is simple, by setting the affinity for every application in TaskManager .. however .. in Ubuntu i just cand find a similar option.. so.. i have no idea how to do that. Tryed to google for that, but i haven't found a solution.. probabbly because i'm not really sure what to search for..
If someone has an idea on what file should i edit, or if there;s an application for ubuntu that can help me accomplish this task.. please tell me what i have to do.
Thank you all in advance.

Marin

---

### Post by mb_webguy on 2010-05-07
I'm assuming you mean "an application running under Wine", since Wine isn't a program.

And no, I don't know of any (easy) way to do what you're asking.  On the other hand, I personally don't see the point.  The linux kernel does a pretty spiffy job of load balancing across multiple CPUs without any user interference.  Also, most apps (especially things like Firefox) put such a small load on a CPU that distributing them by hand is kind of pointless.  If you were talking about a processing-intensive app like a compiler or a video encoder, then it might be an issue -- but again, the kernel is going to pick the CPU that will result in the best balance, and many such programs are now multi-threaded, meaning they'll be split up among the available CPUs.

Manually distributing processes on multiple CPUs seems like a good way to screw things up...

---

### Post by cryptotheslow on 2010-05-07
You should be able to use schedtool to do this. It allows you to launch an app with affinity for whichever core you like.

For e.g. I use it for Urban Terror which sometimes exhibits weird behaviour on multi-core machines.

Once you've grabbed schedtool from the repos it is as simple as creating a new launcher for your app with something like this as the command:

schedtool -a 1 -e /home/noddy/urt/UrbanTerror/ioUrbanTerror.i386

The -a option sets the affinity so the number following will then be 0 or 1. The -e option is used to execute the command after it with the affinity set.

I think you can also set the affinity of already running process with schedtool, but I've never tried that so all I can suggest is "man schedtool" to find out how.

---

### Post by 3rdalbum on 2010-05-07
There is SO little benefit to doing this. If Firefox is using an appreciable amount of CPU, and so is Wine, then they will use a different core anyway.

There's also no need to "wear level" the CPU, because it's not like a single core will wear down or burn out with use. And you'll find single processes will shift between cores on their own anyway due to other factors.

---

### Post by Grenage on 2010-05-07
I would also recommend against this course of action.  Nine out of ten times, you'll reduce performance.

---

### Post by nedmar on 2010-05-10
@cryptotheslow
I tryed shedtools and as advised by mb_webguy, 3rdalbum and Grenage it actually slowed down the computer even more. 
So basically i have to live with it the way it is.. 
Anyway, Thank You all for the support.

Marin

---

