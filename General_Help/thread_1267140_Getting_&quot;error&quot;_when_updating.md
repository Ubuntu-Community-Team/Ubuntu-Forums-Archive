---
title: "Getting &quot;error&quot; when updating"
date: 2009-09-15
forum: General Help
---

### Post by April1212 on 2009-09-15
I have 278 updates that need to be fixed and when i go to get the updates  a window pops up saying:

E: dpkg was interrunpted, you must manually run 'dpkg --configure -a' to correct the problem
E: cache -> open0failed, please report

Can anyone help me.????? 

Thank you very much!
April

---

### Post by April1212 on 2009-09-15
**Getting "error" when updating** 			
 			 			 		   		 		 		I have 278 updates that need to be fixed and when i go to get the updates  a window pops up saying:

E: dpkg was interrunpted, you must manually run 'dpkg --configure -a' to correct the problem
E: cache -> open0failed, please report

Can anyone help me.????? 

Thank you very much!
April

---

### Post by sisco311 on 2009-09-15
Open a terminal (Applications -> Accessories -> Terminal)
and type:
```
sudo dpkg --configure -a
```

---

### Post by April1212 on 2009-09-15
I did that and nothing is happening?

---

### Post by sisco311 on 2009-09-15
> **April1212 said:**
> I did that and nothing is happening?
That's good. :)

Try to update the system again.

---

### Post by April1212 on 2009-09-15
Still the same thing... same window... same everything?

---

### Post by April1212 on 2009-09-15
What is suppose to happen? I am still getting the same error?

---

### Post by plucky on 2009-09-15
> **April1212 said:**
> I have 278 updates that need to be fixed and when i go to get the updates  a window pops up saying:

E: dpkg was interrunpted, you must manually run 'dpkg --configure -a' to correct the problem
E: cache -> open0failed, please report

Can anyone help me.????? 

Thank you very much!
April

Open a terminal **Applications > Accessories > Terminal** and run ```
sudo dpkg --configure -a
``` Enter password which will not be echoed and see if that fixes it. Then run ```
sudo apt-get update
sudo apt-get upgrade
```

Good Luck

---

### Post by plucky on 2009-09-15
> **April1212 said:**
> Still the same thing... same window... same everything?

Copy and paste the output to the forums so we can take a look.

Put it between [noparse]```
Text here
```[/noparse] blocks,so it is easier to read.

Good Luck

[color=red]This problem is solved here[/color]  [http://ubuntuforums.org/showthread.php?t=1267181](http://ubuntuforums.org/showthread.php?t=1267181)

---

