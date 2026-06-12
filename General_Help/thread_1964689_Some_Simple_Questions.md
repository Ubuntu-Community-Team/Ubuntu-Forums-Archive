---
title: "Some Simple Questions"
date: 2012-04-24
forum: General Help
---

### Post by jquillian on 2012-04-24
I installed a program, Kdevlive, but it doesn't show up on any software lists. It does show to be installed. How do I find it and run it?
 
What are the mouse clicks to get to the terminal?
 
Thanks
 
James
'

---

### Post by raja.genupula on 2012-04-24
to open in terminal press ```
CTRL+ALT+T
```
other wise click at the start menu of Kubuntu and type terminal . 

for your program , type the program in the search box too , if it found then type that name in the terminal and press ENTER Key .

if anything comes up , let us know .

---

### Post by jonobr on 2012-04-24
You could also open a terminal window and try

```
which Kdevlive
```

I figure that may show you here it is also.

Cheers

jonobr

---

### Post by jquillian on 2012-04-24
Thanks guys. This is what shows up. 

mike@mike-K52F:~$ Kdenlive
No command 'Kdenlive' found, did you mean:
 Command 'kdenlive' from package 'kdenlive' (universe)
Kdenlive: command not found
mike@mike-K52F:~$ 
mike@mike-K52F:~$ which kdenlive
/usr/bin/kdenlive
mike@mike-K52F:~$ 

If I search for it in the Ubuntu Software Center, it shows up. There is an uninstall button so it must be installed.

---

### Post by techsupport on 2012-04-24
> **jquillian said:**
> Thanks guys. This is what shows up. 

mike@mike-K52F:~$ Kdenlive
No command 'Kdenlive' found, did you mean:
 Command 'kdenlive' from package 'kdenlive' (universe)
Kdenlive: command not found
mike@mike-K52F:~$ 
mike@mike-K52F:~$ which kdenlive
/usr/bin/kdenlive
mike@mike-K52F:~$ 

If I search for it in the Ubuntu Software Center, it shows up. There is an uninstall button so it must be installed.

Did you recently upgrade your Ubuntu from a different release after you installed Kdenlive?

You can uninstall it and reinstall it and see if that helps. Sometimes after upgrading to a newer disto of Ubuntu icons can get lost. That's happened to me before.

---

### Post by jonobr on 2012-04-24
Yep its there alright,
Original query failed due to an uppercase K that wasnt used in the package.

I notice [here]("http://www.kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/ubuntu-packages") that it says, all versions in the repos are deprecated and to install a later version.

Not sure if you want to do that

Cheers

Jonobr

---

### Post by jquillian on 2012-04-24
How do you normally run a program after it is installed?

i just installed OpenShot. There is no button on the right to add it to the programs on the right.

Kdenlive apparently doesn't work with the latest Ubuntu upgrade.

---

### Post by ph4nt0m117 on 2012-04-24
./bin/Kdevlive in terminal

---

### Post by raja.genupula on 2012-04-26
> **jquillian said:**
> Thanks guys. This is what shows up. 

mike@mike-K52F:~$ Kdenlive
No command 'Kdenlive' found, did you mean:
 Command 'kdenlive' from package 'kdenlive' (universe)
Kdenlive: command not found
mike@mike-K52F:~$ 
mike@mike-K52F:~$ which kdenlive
/usr/bin/kdenlive
mike@mike-K52F:~$ 

If I search for it in the Ubuntu Software Center, it shows up. There is an uninstall button so it must be installed.

I thin there you are typing The Big K not small k 
try again with typing as **kdenlive**

---

### Post by gordintoronto on 2012-04-26
James, are you using kubuntu 11.10? If not, what?

One of the tough things to get used to in Linux is that the shift key matters. Desktop and desktop are completely different places.

---

