---
title: "Oneiric. banshee problems."
date: 2011-10-15
forum: General Help
---

### Post by Urichhai on 2011-10-15
Well after doing an upgrade on my asus netbook and a few restarts everything was working sweet,until i started trying to use banshee.
every time I tried to listen to music or watch a video it freezes.
I would start a video from my file and the video would play but the interface would grey out and the only thing that seems to work is the close icon, which brings up the Banshee has stopped working and force quit. I really need my frackin banshee to work. reinstalled 11.4 and guess I will wait for a couple of months to see what happens. New to linux but learning as I go along.
been a while since I have used Ubuntu but finally getting back into it.

---

### Post by philinux on 2011-10-15
Moved to own thread.

---

### Post by rax_m on 2011-10-29
I'm experiencing the exact same issue.. anybody manage to resolve this?

Thanks

---

### Post by bel3atar on 2011-11-01
Same problem with a fresh install...

---

### Post by ballantony on 2011-11-01
Are you connected to the internet when it freezes?  I had that problem on my unconnected laptop.  I've had a temporary fix by switching off the Banshee internet content.  I keep meaning to have a deeper look at what makes this happen

---

### Post by Matthew Bucktrout on 2011-11-10
Ballantony, you're a star. Shame I didn't find your solution to my issue with Banshee this morning instead of this evening - could have saved myself hours of messing about!

I had the same issue with Banshee crashing at the end of the first song of an album on my laptop, but only when I was using the laptop in my workshop. It was fine in the house. The house has WIFI Internet connection, the workshop doesn't, but I hadn't thought of that as a reason why this problem should occur - what's the Internet connection got to do with track changes between files stored on my Hardrive? 

Anyway, followed your advice and switched off the Internet content in preferences in Banshee and now I can listen to my music again in the workshop. This bug only appeared after upgrading to Ubuntu 11.10. Can't remember whether a newer version of Banshee was installed with the upgrade from 11.04, but had no problems under 11.04. 

I had spent hours trying to install the Banshee 2.2.1 version that I found on their website, which said it fixed a load of bugs. But it was in tarball form and I'd never installed using a tarball before. Took me ages to install all the dependencies required by ./configure. 

The [http://banshee.fm/download/development/](http://banshee.fm/download/development/) page has a couple of terminal commands which install MOST of the dependencies (but I didn't find that straight away, so spent a good while looking for each missing package which was thrown up by ./configure one by one using google). There were still one or two which weren't covered by their terminal commands such as "boo", which I eventually found as part of another package on a forum - can't remember which, I went all over the place trying to find it. Suffice to say that the 'boo' package available in the Ubuntu Software Centre ISN'T what it needed - that was installed already but ./configure still wasn't satisfied. 

I was very pleased when I'd finally got all the dependencies in place and was able to [make] and then checkinstall the tarball contents. Had to use [sudo checkinstall --fstrans=0] in the end because [checkinstall] by itself came up with an error and failed. Found out how to do that by reading the Ubuntu Forum thread on how to deal with package installation and tarballs. 

So, got it all installed, and was very disappointed when it WOULD NOT start for toffee. Tried reinstalling it a couple of times, re "made" the package, reinstalled that. Not a sausage. 

So, got rid of the new version I'd tried to get up and running completely using the synaptic package manager. Then reinstalled Banshee 2.2.0 from the software centre and found this thread saying I could have saved myself a lot of time by just switching off the Internet content in my existing installation of Banshee. 

Did that, went to the workshop and hey presto, no problems with track changes. 

:lolflag::guitar:

At least it made me learn about tarballs. I would have been nice if the new version of Banshee had actually WORKED after all that though. Wonder when I did wrong?

Thanks for your hint

Matt

---

