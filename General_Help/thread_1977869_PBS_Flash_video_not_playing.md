---
title: "PBS Flash video not playing"
date: 2012-05-10
forum: General Help
---

### Post by Rebelli0us on 2012-05-10
None of the programs on **video.pbs.org** work in Firefox or Chromium!

But PBS on Firefox running in a Windows VM works fine.

Linux short-changed again?

---

### Post by qamelian on 2012-05-10
Working fine here on Firefox on 12.04. I'm watching Sherlock right now. :)

---

### Post by Rebelli0us on 2012-05-10
Thank you. I'm sticking with 10.10, I can't stand the UI in 12.04, I guess I'll have to run PBS in VBox.

---

### Post by wilee-nilee on 2012-05-10
Make sure you have the codecs you need such as the restricted-extras for your desk top. Also medibuntu added to the repos, and libdvdcss2, and W32-codecs installed.

I have gotten all of PBS on line programming before 10.10 to play, and by the way 10.10 is end of life and not supported, you would be better with 10.04, which is suported for another year, or a Ubuntu above 10.10.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Add the above repo with a change of Ubuntu release, it may work with 10.10, and it may not, not really sure due to the support being stopped. You may not get the extras as of now either running this release if not already installed, hard to say really

You might also try the Firefox addon flash aid and run its wizard this will set up your flash to run best.

Also thanks for the link to that pbs site I did not even know about it, PBS is about all I watch as far as TV goes, that is a nice site.:)

---

### Post by qamelian on 2012-05-10
> **Rebelli0us said:**
> Thank you. I'm sticking with 10.10, I can't stand the UI in 12.04, I guess I'll have to run PBS in VBox.
I'm not a fan of Unity either, but I do prefer Gnome-shell to the old Gnome 2 interface, so that is what I use.

---

### Post by Rebelli0us on 2012-05-10
> **wilee-nilee said:**
> Make sure you have the codecs you need such as the restricted-extras for your desk top. Also medibuntu added to the repos, and libdvdcss2, and W32-codecs installed.

I have gotten all of PBS on line programming before 10.10 to play, and by the way 10.10 is end of life and not supported, you would be better with 10.04, which is suported for another year, or a Ubuntu above 10.10.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Add the above repo with a change of Ubuntu release, it may work with 10.10, and it may not, not really sure due to the support being stopped. You may not get the extras as of now either running this release if not already installed, hard to say really

You might also try the Firefox addon flash aid and run its wizard this will set up your flash to run best.

Thank you. That’s confusing, I don’t even know what Medubintu is. I’m running 64-bit, I have the restricted extras to play commercial DVD movies, but PBS video seems to be Flash-based. I have Flash-Aid btw,but it's not helping here.

I know 10.10 is end-of-life, but 12.04 is definitely out of the question for me.

---

### Post by Frogs Hair on 2012-05-10
I was just watching Nova with flash on Firefox Nightly and Opera works as well . Script blocking extensions can cause problems at times if in use  .  I think PBS only requires flash, but I am not positive .

---

### Post by daslinkard on 2012-05-10
I had this exact same issue until I updated the version of Java on the PC.  After making sure you have the latest Java make sure to close out your Internet and then bring it back up.  This fixed the Flash issue for me.  Good luck!

---

### Post by Rebelli0us on 2012-05-11
> **daslinkard said:**
> I had this exact same issue until I updated the version of Java on the PC.  After making sure you have the latest Java make sure to close out your Internet and then bring it back up.  This fixed the Flash issue for me.  Good luck!

Isn't Java installed automatically by the Update Manager?

---

### Post by Rebelli0us on 2012-05-11
I just launched 12.04 in VM, installed Flash and PBS video works! 

In 10.10 flash is working too, including PBS but the movie's video overlay is blank.

---

