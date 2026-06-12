---
title: "synaptic not opening!!"
date: 2009-08-04
forum: General Help
---

### Post by harivittal.hk on 2009-08-04
hi friends,
i am facing a new serious problem now,i was working with AWN manager for sometime and wanted to install a pidgin screenlet,so tried to open synaptic manager..but its not opening..i even restarted the system..the same problem exists...m not able to see the synaptic even on the dock..
plz help..
any support is appreciated..
:confused:

---

### Post by credobyte on 2009-08-04
Alt + F2:
```
gksudo synaptic
```

Another workaround would be to use Add/Remove ( which pretty much does the same as Synaptic ).

---

### Post by harivittal.hk on 2009-08-04
folks plz help me to get rid of this serious problem...m not able to install software updates nor add/remove anything..
synaptic manager is not opening...
i am really facin serious trouble with this OS here!!
plz help!!**__**

---

### Post by harivittal.hk on 2009-08-04
even add/remove is also not opening,i tried tat & am not able to install software updates also..
plz help!!

---

### Post by harivittal.hk on 2009-08-04
i ran gksudo synaptic also..its not opening!!

---

### Post by harivittal.hk on 2009-08-04
***__***!hi friends,
i am facing a new serious problem now,i was working with AWN manager for sometime and wanted to install a pidgin screenlet,so tried to open synaptic manager..but its not opening..i even restarted the system..the same problem exists...m not able to see the synaptic even on the dock..
plz help..
any support is appreciated..

---

### Post by harivittal.hk on 2009-08-04
folks plz help me to get rid of this serious problem...m not able to install software updates nor add/remove anything..
synaptic manager is not opening...
i am really facin serious trouble with this OS here!!
plz help!! m really gettin beaten here!!:(:confused:

---

### Post by michy99 on 2009-08-04
> **harivittal.hk said:**
> i ran gksudo synaptic also..its not opening!!

Did you get any error message?

---

### Post by harivittal.hk on 2009-08-04
no i didnt get any error messages...its appearing lik a flicker n disappears....:(

---

### Post by martinbaselier on 2009-08-04
What happens when you run the command? Pasting the errormessage would be helpful.

Also **sudo synaptics** will do the trick just fine, you don't need gksudo unless you prefer to enter your password in a gui.

---

### Post by harivittal.hk on 2009-08-04
no folks nothin..its not opening even on running as
   "sudo synaptic"
no error messages,nothin.

---

### Post by 1/0 on 2009-08-04
What happens if you open a terminal and enter:

```
sudo synaptic
```

enter your password when prompted and press enter?

[edit]Seems it was a quadruple post that got merged...[/edit]

---

### Post by TeoBigusGeekus on 2009-08-04
Ignore this post

---

### Post by ugm6hr on 2009-08-04
Open terminal

Ensure everything is installed correctly:

```
sudo apt-get update
sudo apt-get install --reinstall synaptic
```

Then try running it:

```
gksudo synaptic
```

---

### Post by martinbaselier on 2009-08-04
What does
**ps -e | grep synaptic -i**
show? 

If it shows up, you can kill the process:  

**killall synaptic -KILL**

You could try a reinstall: 
**sudo apt-get install synaptic --reinstall**

or completely remove it and then install it again:
**sudo apt-get purge synaptic**

Make sure to install all removed packages again. 

In my case these are the ones: (I'm running xubuntu though and not gnome)

**sudo apt-get install synaptic ubufox apturl gnome-app-install gnome-codec-install language-selector software-properties-gtk**

---

### Post by jmszr on 2009-08-04
harivittal.hk,

I had a similar problem and the fix was:```
sudo rm /var/cache/apt/*.bin
```

Hope that helps.

---

### Post by harivittal.hk on 2009-08-04
Thanks a lot to everyone for timely help..
I fixed the problem..
Opensource rocks!!:p

---

### Post by 1/0 on 2009-08-04
> **harivittal.hk said:**
> Thanks a lot to everyone for timely help..
I fixed the problem..
Opensource rocks!!:p

Which of the solutions worked for you?

---

