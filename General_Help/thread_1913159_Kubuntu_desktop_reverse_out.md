---
title: "Kubuntu desktop reverse out"
date: 2012-01-22
forum: General Help
---

### Post by oldgreygary on 2012-01-22
I haven't been happy with the Unity desktop so I thought that I would install the kubuntu desktop to see if that would be better.

I think that I have not fully understood the implications of this. Although I have two options available where I can choose either Unity or Kubuntu (KDE) desktops they don't seem to be compatible.

When I run the Kubuntu desktop changing the monitor or font settings causes the system to hang. Same on Ubuntu/Unity. 

So, I was wondering how do I get back to pre-Kubuntu desktop install? I have tried uninstalling the Kubuntu desktop but this makes no difference. Or would it be better to do a fresh install of either Ubuntu/Kubuntu to get back to where I was? Firstly, backing up my data files of course?

Any thoughts apart from me being a numpty for doing this!!

Cheers for now

Gary

---

### Post by raja.genupula on 2012-01-22
Always Fresh install is a Final solution.

So if you choose kubuntu-desktop then in terminal do this

sudo apt-get install --reinstall kubuntu-desktop

if you want to keep only one desktop wither Ubuntu or Kubuntu then use this link .

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by oldgreygary on 2012-01-23
The problem seems to be that having two desktops is a mismatch. After downloading the Kubuntu-desktop when I boot up I now get an initial screen which displays the Kubuntu logo, In the login screen I have the option of choosing the KDE or Ubuntu options. If I choose Ubuntu I get the Unity style desktop, If I choose KDE then I get that. But if I choose the KDE option the display is not correct. If I try changing this using the monitor option in system settings  this causes the system to hang. In effect the KDE option is unusable. Kubuntu-desktop is all that I have installed which is why I wanted to reverse this change out. Unless there are some options/suggestions that can make the KDE workable.

To summarise. I have downloaded kubuntu-desktop to my Ubuntu 11.10 installation which was using the Unity desktop. The Unity desktop still works ok. But the KDE screen size cannot be changed as it causes the system to hang.

3 question from this:

1. Have I made a mistake by trying to run the KDE desktop on the Ubuntu 11.10 system?

2. Is there a solution to fix why I cannot change the display/monitor options in KDE? If there is no solution then question 3 applies.

3. Can I backout the kubuntu-desktop so that I am back to a Ubuntu/Unity desktop only?


Gary

---

### Post by raja.genupula on 2012-01-23
> **oldgreygary said:**
> The problem seems to be that having two desktops is a mismatch. After downloading the Kubuntu-desktop when I boot up I now get an initial screen which displays the Kubuntu logo, In the login screen I have the option of choosing the KDE or Ubuntu options. If I choose Ubuntu I get the Unity style desktop, If I choose KDE then I get that. But if I choose the KDE option the display is not correct. If I try changing this using the monitor option in system settings  this causes the system to hang. In effect the KDE option is unusable. Kubuntu-desktop is all that I have installed which is why I wanted to reverse this change out. Unless there are some options/suggestions that can make the KDE workable.

To summarise. I have downloaded kubuntu-desktop to my Ubuntu 11.10 installation which was using the Unity desktop. The Unity desktop still works ok. But the KDE screen size cannot be changed as it causes the system to hang.

3 question from this:

1. Have I made a mistake by trying to run the KDE desktop on the Ubuntu 11.10 system?

2. Is there a solution to fix why I cannot change the display/monitor options in KDE? If there is no solution then question 3 applies.

3. Can I backout the kubuntu-desktop so that I am back to a Ubuntu/Unity desktop only?


Gary

for 3 Questions i can answer two
1.Ans: It will going to install silently . so no possibility.
3.Ans:in the above post of mine i have given you link for pure Gnome. use that .

---

### Post by oldgreygary on 2012-01-23
Thanks for your help. I used the option you gave to backout to pure Gnome which has worked. I had to re-install some packages but thats fine.

Thanks

Gary

---

### Post by raja.genupula on 2012-01-23
you're welcome man , please mark the thread as solved from thread tools.

---

