---
title: "I can't install anything,Ubuntu says the app is untrusted!!!"
date: 2011-03-25
forum: General Help
---

### Post by PCaddicted on 2011-03-25
Hi,
I have managed to fix the problem where Ubuntu did not recognize my admin password,but now I have another problem.I tried to install an application from the Ubuntu Software Center.I entered my admin password, when I was asked to do it.Then,I got this message:

[I]''[B]Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.'[/B]'[/I]

And I am not allowed to install the program.It happens regardless of the app I'm going to install-thus I can't install anything!
As described before,I use Ubuntu 10.10.
[SIZE=3]**Please help me!**[/SIZE]

---

### Post by alphaamanitin on 2011-03-25
Have you enabled the restricted packages?  The multiverse and universe packages?  This could be the issue I think.  You can enable those packages by going to the Synaptic Package Manager under Systems:Administration.  

AlphaA

---

### Post by PCaddicted on 2011-03-25
I don't really understand how to do that-I'm relatively new to Ubuntu:confused:.Please give me more details about what should I do once I get to the Synaptic Package Manager.

---

### Post by 5149.5 on 2011-03-25
The OPs error is due to the Ubuntu keyserver being down. It has been down all week. WTH? I understand that things happen to servers but this is just @#$%^poor.

---

### Post by oldos2er on 2011-03-25
> **PCaddicted said:**
> [I]''[B]Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.'[/B]'[/I]

And I am not allowed to install the program.

Open a terminal (Applications, Accessories, Terminal), run ```
sudo apt-get update
``` If that doesn't fix the error, use either Synaptic Package Manager or apt-get to install your packages. They will still show warnings, but allow you to install anyway. I don't know why Software Center chokes on this.

---

### Post by polardude1983 on 2011-03-25
Try clicking on the top bar System>Administration>Update Manager

Once loaded click the settings button on the bottom left

Click the updates tab on the new pop up screen

and make sure Unsupported Updates is checked

---

### Post by B Crowther on 2011-08-18
"Once loaded click the settings button on the bottom left

Click the updates tab on the new pop up screen

and make sure Unsupported Updates is checked"

Excellent! That did it.  Though why the update balked this time when it has been loading dailies for Chromium for yonks without complaint beats me.

---

### Post by frncz on 2011-08-18
The advice above is probably useful.
It is however a shame that you received this very unhelpful message when trying to install applications (I was also faced with it, and perplexed as to what to do). The message should be replaced by something more helpful, with links to the solution.
Any possibility of improving this, Ubuntu?

---

### Post by oldos2er on 2011-08-18
To bring your idea to the developers' attention, check [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

---

