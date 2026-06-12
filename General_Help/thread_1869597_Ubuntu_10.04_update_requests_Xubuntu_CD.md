---
title: "Ubuntu 10.04 update requests Xubuntu CD"
date: 2011-10-26
forum: General Help
---

### Post by graham bowers on 2011-10-26
Hello
I have run the LTS versions of Ubuntu since 2007 and so have been running 10.04 since it became available. 
I downloaded the Xubuntu 11.04 ISO and burnt it to a CD using this machine,for use on an older laptop. Out of curiosity I ran up the live CD on this machine (my Ubuntu 10.04 desktop).

I ran the update manager on this machine when invited to do so and got a message requesting me to "Insert disc labelled Xubuntu 11.04 Natty Narwhal release i386120110427".

I bombed out of the update process. I'm guessing that running 11.04 in live CD mode has done something unintended (by me anyway).

So, now the questions please:
1) Can I do anything to stop the update process requesting the Xubuntu CD and if so, what?
2) If I succumb and put in the Xubuntu CD as requested, is anything bad likely to happen?
3) Any other bright ideas please?

Oh, and I am Ubuntu only, so this machine is not dual booted. If it all goes pear shaped I will still have internet access on the laptop through Xubuntu though.

Thanks
Graham

---

### Post by elliotn on 2011-10-26
it may happen that u have added the xubuntu as a repo in your repository, check if u haven't and if u have remove it. I had the same issue in 10.04 but mine was caused by the fact that I used the dpkg-repack backup trick to back up my packages in 9.10 so whenever I update I had to have the 9.10 cd but I don't know how I fixed it

---

### Post by graham bowers on 2011-10-26
Thanks elliotn, you were spot on.
I went in to the synaptic package manager and removed the repository.
Cheers
Graham

---

