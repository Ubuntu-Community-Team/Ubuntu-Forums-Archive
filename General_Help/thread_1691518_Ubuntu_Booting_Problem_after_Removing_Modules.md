---
title: "Ubuntu Booting Problem after Removing Modules"
date: 2011-02-20
forum: General Help
---

### Post by Nipuna on 2011-02-20
Hello

I am Using Ubuntu 10.10 And I installed some Modules to Install Realtek Audio drivers. (I didn't have sound Problems But I installed them :) )

Then when i tried to boot there were More names in Boot menu. So I removed Installed modules and then restarted and Computer worked well.

But Yesterday 1 Day after Installing Modules, I tried to boot then it says this.



```


There are so many thing but i don't remember them :)

At the end of the message there is something like this

BusyBox v.1.15.3    and more.......

At the very end there is This message,

(iaitrarfs)_


```Can you Help me to fix this If Not I have to Install Ubuntu Again. :confused:

I have Internet for Ubuntu.




Thanks

---

### Post by wilee-nilee on 2011-02-20
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by Nipuna on 2011-02-20
Thanks friend I will try and tell you

---

### Post by Nipuna on 2011-02-20
I left the script to run about 10 minutes but still this no result.txt file :confused:

```

ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh 
Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 
Searching sda8 for information...

```

---

### Post by Nipuna on 2011-02-20
No result.txt i think i was running it for 30Mins 

I stopped it.

still this

```
 
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh 
Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 
Searching sda8 for information... 

```

Any Help?

---

### Post by Nipuna on 2011-02-20
I tried to Mount my Previous Ubuntu Partition and It can't be mounted and I think this Might be the Problem that Script can't Work properly.

Now I remember a little bit that was,

When I was working on Ubuntu Power has gone and My DAMN UPS turned off too. I think my Ubuntu Partition is corrupted.

i am  Going to format it.

Can't i do anything without formatting?

There is another problem that is my Ubuntu CD isn't working well too. I can start Live session but can't install if I try to install it stuck on the welcome Screen.  And Can't restart too. it doesn't go beyond from the restating screen. I have to manually press my computer's Restart button to Restart when i use Live CD.

is there any way to Correct this too. Because i don't want to download another Ubuntu 10.10 version I will download when there will be 11.04 :)



Thanks

---

