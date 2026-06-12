---
title: "gDebi installer not working?"
date: 2009-09-04
forum: General Help
---

### Post by Mad dog on 2009-09-04
Any time I try to download and install a .deb package I get this message: 

"[package-name].deb could not be opened, because the associated helper application does not exist. Change the association in your preferences."

I already tried reinstalling the gdebi and the gdebi-core from the Synaptic thing, and it didn't help.

I've been using Ubuntu for about six months now, and am really enjoying it, this is just another problem I know you guys can help me with.

---

### Post by Mad dog on 2009-09-04
Hmm... I was mistaken, it works if I save the file first and then install it, but for some reason, my Firefox can't use it/find it. Any ideas?

---

### Post by CatKiller on 2009-09-04
> **Mad dog said:**
> Any ideas?

Yes. Do this.

> **Mad dog said:**
> it works if I save the file first and then install it

---

### Post by catskul on 2009-11-19
Thats a terrible answer. 

There is clearly something wrong, and he obviously knows that he can install via work around, but wants to fix the underlying problem.

Not that I know what the issue is. I have the same problem.

---

### Post by CatKiller on 2009-11-21
> **catskul said:**
> Thats a terrible answer. 

It's one that works, simply. I have no idea what your criteria for a good answer might be, but I doubt they are any better than that.

> Not that I know what the issue is.

Then why are you commenting on the quality of someone else's answer?

I **do** know what the issue is, and that is still the best solution.

You *could* tart around for a while changing Firefox's application associations so that it knows what to do with .deb files (the underlying problem), or you could change nothing and use the method that works. It's not like having Firefox open gDebi is somehow magically better than having Gnome open it, except that it's more hassle to set up.

---

### Post by taurelas on 2010-05-04
I sorted this out in few easy steps:


[LIST=1]
[*]When Firefox asks to open/save *.deb, choose **Save** and mark **Do this automatically(...)**
[*]Go to **Edit->Preferences**, and then **Applications** and find **Software package**.
[*]From the menu on the right, choose **Use other**...
[*]In location field, enter **/usr/bin/gdebi-gtk **and press **Open...**
[*]**Close**
[/LIST]
 
Hope this helps and saves few *unnecessary *clicks ;-)

---

### Post by wyrless2002 on 2010-06-05
taurelas, Thanks. You're the kind of community member that "they" (all the bloggers and media) associate with Ubuntu and Open Source. This is proof that  having 1 bean, er, post, that is helpful and polite trumps  posting 4000 times to the forums with a snarky attitude. 

I've actually tried to remedy this same issue through the **Edit> Preferences> Applications** tab, but wasn't able to get it to work that way. I went to the Applications tab and then put the word PACKAGE into the search box and I get 4 different types of software packages, application/binary, application/x-archive, application/x-deb, application/x-debian-package. I used the same method you describe on the last two .deb types, closed Firefox, and was not able to fix the problem.

What I had to do was click on the file (link) that I was trying to install from the website I was on, and when it brought up the **"What should Firefox do with this file?"** menu, I chose **Open with> Other...** and then navigated to **usr/bin/gdebi-gtk** like you posted above, clicked **Open** and then chose **Do this automatically for files like this from now on**, before clicking **OK**.



It's been broke for some time now, but you helped me think it through and try something different.

---

### Post by rykel on 2010-08-25
My question is, WHY do we even have to do any of the above, when gdebi used to work out of the box with older versions of Ubuntu/Firefox?

---

### Post by rykel on 2010-08-26
Hi, I managed to get gdebi to be the default dialog again by purging Firefox from the system, and then reinstalling it. In my case, I upgraded from Karmic to Lucid, and so Firefox was still running on old Karmic settings.

---

