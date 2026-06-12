---
title: "How to install skype on my ubuntu 8.04"
date: 2010-11-04
forum: General Help
---

### Post by Iyanysha on 2010-11-04
Hi All,

I need help!!!

I have dowloaded skype from skype.com for ubuntu 32bit but when I try to install it on my it sais error: Dependency is not satisfiable:libasound2.

How to fix this problem?

Thanks in advance for help!!!!:)

---

### Post by lombaardcj on 2010-11-04
Hi,

I know you already did the download, but if you want to try, why not use Synaptic Package Manager to install Skype.  Just search for it, select and install.

The alternative would be to use the command line and type in:

```
sudo apt-get install skype

```The rest should be taken care of for you with regards to dependencies and installation.

I have upgraded from 8.04 to latest, and my Skype is still working 100%

Hope you this a solution to your problem.

Regards,
Chris

---

### Post by Segofam on 2010-11-04
> **lombaardcj said:**
> I have upgraded from 8.04 to latest, and my Skype is still working 100%

Can you tell us what the latest version of Skype is for Ubuntu?

---

### Post by kirkface8 on 2010-11-04
> **Segofam said:**
> Can you tell us what the latest version of Skype is for Ubuntu?
[sudo apt-get build-dep skype[/code]

then run the file you downloaded

---

### Post by Segofam on 2010-11-26
> **kirkface8 said:**
> [sudo apt-get build-dep skype[/code

kirkface8: what is and where do we find the "/code"?

---

### Post by James78 on 2010-11-26
> **Segofam said:**
> kirkface8: what is and where do we find the "/code"?
That was a spelling error and was supposed to look like this.
```
sudo apt-get build-dep skype
```

Honestly though, I don't see why installing the build dependencies for skype is of any use. You wanted to know what the version was, do this to figure that out. Or you can just find it in Synaptic.
```
apt-cache show skype
```
As the other person said earlier, to install just
```
sudo apt-get install skype
```

---

### Post by I'mGeorge on 2010-11-26
> **Iyanysha said:**
> Hi All,

I need help!!!

I have dowloaded skype from skype.com for ubuntu 32bit but when I try to install it on my it sais error: Dependency is not satisfiable:libasound2.

How to fix this problem?

Thanks in advance for help!!!!:)

it's because you're mising the libasound2 dependency. Open synaptic and search for it, and see if it's installed. If it's not than install it, if it's installed and still asks for it when you're trying to install skype install libasound2-dev also and it should work.

---

### Post by Penguin=) on 2010-11-26
Try downloading it from the Ubuntu Software Center.

---

### Post by jdneate on 2011-01-14
I know that this issue was raised some time back but just in case it is of interest, I had the same problem trying to load Skype on Ubuntu 8.04 a couple of days ago.

The download on the Skype web site specifically referenced 8.04 LTS - so I had expected it to be straightforward.

After I hit the problem I followed the advice on this thread trying sudo this and that.

When this didn't work, I found a previous version of Skype (2.0.0.68-1)  on the internet ( not easy). This doesn't produce the download error and Skype seems to work.

Could the reference on the Skype web site to 8.04 be in error ?

---

### Post by jdneate on 2011-01-14
I know that this issue was raised some time back but just in case it is of interest, I had the same problem trying to load Skype on Ubuntu 8.04 a couple of days ago.

The download on the Skype web site specifically referenced 8.04 LTS - so I had expected it to be straightforward.

After I hit the problem I followed the advice on this thread trying sudo this and that.

When this didn't work, I found a previous version of Skype (2.0.0.68-1)  on the internet ( not easy). This doesn't produce the download error message and Skype seems to work.

Could the reference on the Skype web site to 8.04 be in error ?

---

### Post by Segofam on 2011-01-14
I think that when the site was updated (back then) it was probably set to a version that they tried, and when it worked, they set it on the web page with that version in mind.
This MSI Laptop has Skype 2.1.0.81, and though it works fine, it is now where near as good as the version that my home pc with Win 7 has running on it.
It appears to me that, after updating numerous times over the past year or so, that there is no more recent version available.
My suggestion is that 8.04 was for an earlier version of Ubuntu!

---

