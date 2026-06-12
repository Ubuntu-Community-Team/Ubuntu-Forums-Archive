---
title: "Youtube + iplayer play button"
date: 2010-07-27
forum: General Help
---

### Post by Someone uk on 2010-07-27
Hi, i assume this is a problem with flash but when go to the iplayer website there is a problem with the play/pause button and almost every other button on the video applet 
i have a much more unusual problem with youtube, the videos work fine when i veiw them through someone's profile (like [this]("http://www.youtube.com/user/NixiePixel#p/u/9/f2wFjPy-wAA")) however i could try watching the same video in the main area where comments are viewed and posted etc and the buttons become in the applet completely dysfunctional ([like here]("http://www.youtube.com/watch?v=f2wFjPy-wAA"))

any ideas?

---

### Post by HRH_H_Crab on 2010-08-08
I think I have the same issue.
I cannot for the life of me get iplayer to work properly.
I can install the iplayer desktop (which is pretty awful really) and download stuff and play it, but I cant stream from the BBC website.

Its working on my old Ubuntu install just fine, so I assume this is due to Adobes recent massive security balls ups and then ludicrously unhelpful decision to pull all 64-bit Linux support.

Is this the same company that claimed they were cross-platform champions when Apple had a go?

---

### Post by HRH_H_Crab on 2010-08-08
Maybe this isn't actually a Flash problem.
I've just discovered that its working in Chrome.
Still broken in Firefox.

Odd...

---

### Post by davecykl on 2010-08-12
I've just encountered a similar problem after an update to Flash.

After some searching, I found a pointer to the following bug report in Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/410407](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/410407)

The *[FONT=Lucida Sans Unicode]export GDK_NATIVE_WINDOWS=1[/FONT]* workaround suggested in the bug description seems to have resolved the problem for me.

(I understand that the reason that Chrom* doesn't have the Flash problem is because Flash is integrated into Chrom* in a different way than is done in browsers which use the normal Netscape plugin mechanism.)

---

