---
title: "Package issues.."
date: 2011-02-21
forum: General Help
---

### Post by Steam. on 2011-02-21
Whenever I try to install anything, it says an error about broken packages, with run in terminal sudo synaptic or sudo apt-get install -f.I did the install -f thing, and this popped out.

[IMG]http://i51.tinypic.com/zvyarq.jpg

The following essentials packages packages will be removed is e2fsprogs.

I checked  the synaptic for broken packages, and it showed e2fsprogs along with 3 others.There isn't a reinstall option available, so im asking if it's safe to delete it so I can install my stuff?

Please answer.

Edubuntu 7.04 btw.I also tried to upgrade and the same error popped out.

---

### Post by Steam. on 2011-02-21
I know this hasn't passed 24 hours, but I will bump this because rarely anyone scrolls down to see other topics.

---

### Post by Steam. on 2011-02-21
> **Steam. said:**
> I know this hasn't passed 24 hours, but I will bump this because rarely anyone scrolls down to see other topics.


Anyone?

---

### Post by Steam. on 2011-02-21
I know that i'm annoying, but I really need this.

---

### Post by Diametric on 2011-02-21
I might recomment running apt-get with the check argument.  Read the man page for this usage, as I believe that is what is used to make sure there are no broken dpendancies.  Also, if I'm reading your question right, you can delete the applications you no longer use.  Apt-get or aptitude should* resolve your dependancies

---

### Post by Steam. on 2011-02-21
I ask if it's safe to delete e2fsprogs,cause that's broken.

---

### Post by Diametric on 2011-02-21
A quick search shows that e2fsprogs is used in the ext2 file system:  [http://e2fsprogs.sourceforge.net/](http://e2fsprogs.sourceforge.net/)
 
I might do a bit if research until someone more knowledgeable then myself can chime in here.  I have not encountered this program before.

---

### Post by Steam. on 2011-02-22
Anyone?

---

### Post by Steam. on 2011-02-22
Oh come on.

---

### Post by gordintoronto on 2011-02-22
> **Steam. said:**
> Whenever I try to install anything, it says an error about broken packages, with run in terminal sudo synaptic or sudo apt-get install -f.I did the install -f thing, and this popped out.

[IMG]http://i51.tinypic.com/zvyarq.jpg

The following essentials packages packages will be removed is e2fsprogs.

I checked  the synaptic for broken packages, and it showed e2fsprogs along with 3 others.There isn't a reinstall option available, so im asking if it's safe to delete it so I can install my stuff?

Please answer.

Edubuntu 7.04 btw.I also tried to upgrade and the same error popped out.

Your screenshot does not show the useful information.

---

### Post by Steam. on 2011-02-23
What is there to say?

Whenever I try to install ANY PACKAGE, it shows me there are broken dependencies.Try running sudo synaptic or sudo apt-get install -f in order to fix them.I run sudo apt-get install -f, that shows up.I ran sudo synaptic, tried to mark them for reinstallation, it removes those brlltty and gnome power manager and etc etc.Question is, when I remove them, will I be able to reinstall them back via Update Manager?

There are tons of packages which are in the section removable/uninstallable, sorry it's hard to translate it because the OS is in my language.Those in the removable section are being removed whenever i try to reinstall/delete one of those broken packages.Those "removable"packages are those in the first screenshot.

---

### Post by Steam. on 2011-02-23
Updated last post.

---

### Post by Steam. on 2011-02-24
...

If I could set ubuntu instead of edubuntu up there, i am sure i would get more replies.

---

### Post by oldos2er on 2011-02-24
7.04 reached its end of life a long time ago, unless you're using the old releases repos, I'm kind of surprised you're able to install anything at all.

You should think about upgrading to 10.04 or newer. Sorry this advice doesn't directly address your problem.

---

### Post by frotzed on 2011-02-24
> **Steam. said:**
> Edubuntu 7.04...
Not being snarky, but I have the feeling that you're going to continue to run into frustrations regarding software in the repos if you continue to run a four year-old version of Ubuntu.  Upgrading to 10.04 or newer would save you a lot of headache and may even be the best solution to your issues.

---

