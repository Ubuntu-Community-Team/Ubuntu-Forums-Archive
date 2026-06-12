---
title: "PLF Keys?"
date: 2006-06-03
forum: General Help
---

### Post by lukew on 2006-06-03
Hi,

Am I cracking up or what?? ](*,)  I can not find the PLF GPG Keys.

Thanks

Luke

---

### Post by lukew on 2006-06-05
Am I right in thinking that no one is using the PLF (Penguins Liberation Front) repository with valid GPG Keys?

Surely at least one person can comment on this.

Thanks

Luke

---

### Post by blackjack6.21.91 on 2006-06-05
The PLF has the following text on their website.

> Keys
All PLF packages are signed with the project key. You can download it [there.]("http://plf.zarb.org/plf.asc") In order to have urpmi automatically check the packages during installation, you have to configure your system first.

---

### Post by lukew on 2006-06-05
Tanks for your reply.

Does importing GPG keys with URPMI have any effect on deb repositories?

I am confused as to what to do to verify debian packages within th ubuntu plf repository. Normaly I import them with gpg.

Can anyone shed some light as to what Ubuntu users are supose to do? Is it safe to use URPMI and then import deb packages?

Thanks

Luke

---

### Post by lukew on 2006-06-07
I have tried the following, both seem to port the keys ok

wget [http://plf.zarb.org/plf.asc](http://plf.zarb.org/plf.asc) && sudo gpg --import plf.asc
 AND 

wget [http://plf.zarb.org/plf.asc](http://plf.zarb.org/plf.asc) && sudo apt-key add plf.asc


Though I am still getting....

WARNING: The following packages cannot be authenticated!
  libdvdcss2 w32codecs
Install these packages without verification [y/N]? n
E: Some packages could not be authenticated


Any one know how to import this? Any help would be greatly apreciated.

Thanks

Luke

---

### Post by lukew on 2006-06-08
I looked at the code for easyubuntu and after importing the gpg key, the same was as I have mentioned using apt, it then uses the install along side --force.

Can anyone shed any more light onto the siutation?

Thanks 

Luke

---

### Post by xp_newbie on 2006-08-10
> **lukew said:**
> 
Can anyone shed any more light onto the siutation?


I am afraid that the problem in this situation is more fundamental.

Even if I had working GPG keys, I am not sure I would use them.

Why? 

Because the fact that you can get keys from a particular web site does not necessarily mean that you can trust the people behind it. It only means that whatever you download from that web site can be verified to be as coming from there.

Are you sure the PLF people are trustworthy? After all, they are doing something that is against the law in some countries... I know that the law in the USA sucks (represents the interests of a bunch of filthy rich people only), but the reality is that the PLF folks have to keep their profile low as not to be prosecuted - hence, you can't really verify their credibility.

Are you sure that none of the stuff downloaded from PLF contains malicious code?

It seems that in light of this I shed more darkenss than light. :(

If someone can shed some real light on this, it would be great.

---

