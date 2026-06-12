---
title: "Can I hide Panel"
date: 2012-07-04
forum: General Help
---

### Post by rickm1945 on 2012-07-04
Is there a way to hide the panel to make more room on my laptop screen?

---

### Post by msammels on 2012-07-04
What version of Ubuntu are you using? If it's Ubuntu 12.04 with Unity, then no. You would need to install something such as LXDE or XFCE.

---

### Post by rickm1945 on 2012-07-05
> **msammels said:**
> What version of Ubuntu are you using? If it's Ubuntu 12.04 with Unity, then no. You would need to install something such as LXDE or XFCE.
  I am running Ubuntu 12.04, I though I was using unity. I have hidden the panel and it opens with the bump of the cursor on the left side. How can I find out what I am using for my desktop?

---

### Post by msammels on 2012-07-05
Oh, you mean that panel. When you say "find out what I'm using", what do you mean? Operating system wise or...?

---

### Post by rickm1945 on 2012-07-05
> **msammels said:**
> Oh, you mean that panel. When you say "find out what I'm using", what do you mean? Operating system wise or...?
I meant am I using KDE, unity or what? Is there a terminal command to find out what desktop I'm using?

---

### Post by msammels on 2012-07-05
I'm not sure on that one. If you post a screenshot here, I'll be able to identify it for you :)

---

### Post by vasa1 on 2012-07-05
> **rickm1945 said:**
> I meant am I using KDE, unity or what? Is there a terminal command to find out what desktop I'm using?

When you log in, you have to enter your password and **then** hit enter. **Before** hitting enter, click on the little circular design next to your name (on the right hand side). You'll see a few choices then: Ubuntu = Unity 3D, Unity 2D, and possibly some other choices depending on what you have installed on your computer.

So you should fully know what you will be using in a particular session.

Mostly, you won't be running KDE unless you've installed Kubuntu instead of Ubuntu or added the Kubuntu desktop post-installation.

---

### Post by vasa1 on 2012-07-05
BTW, there is a command to enter in the terminal. It was posted yesterday or so. Let's see if I find it or the poster reads this thread.

Okay, this is what I think it is:
```
echo $DESKTOP_SESSION
```
I read it here: [http://ubuntuforums.org/showpost.php?p=12072611&postcount=2](http://ubuntuforums.org/showpost.php?p=12072611&postcount=2)

Right now, I'm in an xfce session so I see **xfce** as the response.
Yesterday, I was in an Ubuntu (Unity 3D) session and **Ubuntu** was the response.

---

### Post by msammels on 2012-07-05
Yeah, $DESKTOP_SESSION will return something kubuntu, if that's your flavour.

---

### Post by rickm1945 on 2012-07-05
> **msammels said:**
> Yeah, $DESKTOP_SESSION will return something kubuntu, if that's your flavour.
Thanks

---

### Post by rickm1945 on 2012-07-05
> **rickm1945 said:**
> Thanks
How can I install xfce for exmaple to see which desktop I might like the best. I am using Ubuntu 2D right now.

---

