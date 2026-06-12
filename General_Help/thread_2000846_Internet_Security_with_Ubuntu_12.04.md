---
title: "Internet Security with Ubuntu 12.04"
date: 2012-06-10
forum: General Help
---

### Post by Heretika on 2012-06-10
Hi, Ubuntu community.

Recently, I stumbled upon [Tails]("https://tails.boum.org/index.en.html"). Since privacy is a big concern in my country, I'd like to have the security that Tails provides, but at the same time enjoy Ubuntu 12.04. So assuming that one gets a new laptop and installs 12.04 on it, what does one have to do to secure himself to the same or almost the same level as Tails would?

Also, how does one make instant messaging secure?

And furthermore, I still want to use Firefox instead of the Tor browser. So what add-ons should I install to have the same security as Tor users?

Thanks in advance.

---

### Post by codemaniac on 2012-06-10
> **Heretika said:**
> Hi, Ubuntu community.

Recently, I stumbled upon [Tails]("https://tails.boum.org/index.en.html"). Since privacy is a big concern in my country, I'd like to have the security that Tails provides, but at the same time enjoy Ubuntu 12.04. So assuming that one gets a new laptop and installs 12.04 on it, what does one have to do to secure himself to the same or almost the same level as Tails would?

Also, how does one make instant messaging secure?

And furthermore, I still want to use Firefox instead of the Tor browser. So what add-ons should I install to have the same security as Tor users?

Thanks in advance.
Ubuntu Basic security guide can help you get started ,

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

For instant messaging using tor see the below link .

[https://trac.torproject.org/projects/tor/wiki/doc/TorifyHOWTO/InstantMessaging](https://trac.torproject.org/projects/tor/wiki/doc/TorifyHOWTO/InstantMessaging)

However no tools or protocols can promise you complete anonymity over the public tunnel of Internet .They are here only to add more steel to your bullet proof jacket .

---

### Post by Cavsfan on 2012-06-10
I would install Noscript, WOT, Biscuit (Preserve the cookies you do not want to delete) and Better Privacy to control flash cookies.
Noscript is a bit of a pain to initially setup, there is a Youtube video you can watch. But, It will give you total control over which sites can execute scripts in Firefox.
WOT is fairly good at telling you which sites are good and bad with green circles by good sites and red circles by bad sites. 
It is just normal people rating the sites so, it is not perfect.

Those are 4 good addons for Firefox security.

---

### Post by Heretika on 2012-06-10
Thank you for the replies.

I have a question, though. In the Basic Security page in the Ubuntu Wiki, it's said that one shouldn't use hardware acceleration in Firefox for extra security. Why?

---

### Post by Cavsfan on 2012-06-10
> **Heretika said:**
> Thank you for the replies.

I have a question, though. In the Basic Security page in the Ubuntu Wiki, it's said that one shouldn't use hardware acceleration in Firefox for extra security. Why?

Not sure. I haven't seen it but, I apparently am not using it and I don't need it as Firefox 13 is ultra fast.
I think it gets bogged down if you add too many addons. I only have the ones mentioned above and my FF is smoking.

---

### Post by brainwash on 2012-06-10
> **Heretika said:**
> I have a question, though. In the Basic Security page in the Ubuntu Wiki, it's said that one shouldn't use hardware acceleration in Firefox for extra security. Why?
The implementation (based on OpenGL) is not very stable and causes many problems on Linux systems. Only the proprietary NVIDIA driver has not been blacklisted and should support hardware acceleration in Firefox.
Type "about:support" in the address bar, scroll down to the "Graphics" section and check the value of "GPU Accelerated Windows" (0 means disabled).

---

### Post by Cavsfan on 2012-06-10
I didn't even know Firefox had hardware acceleration. Mine is not turned on and I have the latest nVidia (version-current-updates) version 295.49.
I have Cairo Dock open GL, Compiz maxed out with Emerald windows manager and nary a problem.
I can't imagine the usefulness of Firefox hardware acceleration.

---

### Post by codemaniac on 2012-06-11
> **Heretika said:**
> Thank you for the replies.

I have a question, though. In the Basic Security page in the Ubuntu Wiki, it's said that one shouldn't use hardware acceleration in Firefox for extra security. Why?

&#8220;Hardware acceleration&#8221; is basically using the GPU when it&#8217;s possible (instead of the CPU). This makes page-drawing operations faster. I dont know if there are any security issues involved in it .I think other members can comment better .

---

