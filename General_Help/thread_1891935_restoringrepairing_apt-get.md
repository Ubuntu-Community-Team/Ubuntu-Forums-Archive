---
title: "restoring/repairing apt-get"
date: 2011-12-06
forum: General Help
---

### Post by earl100 on 2011-12-06
I use Ubuntu 11 on a Toshiba netbook- 1 GB ram, 250GB drive.

I can download from the internet as usual, but cannot use Ubuntu's software center to download programs...something seems wrong with my installation of apt-get.

Any suggestions as to how I can restore/repair it?

Earl

---

### Post by phidia on 2011-12-06
What specifically are you seeing when you try to use the software center?

Can you open the terminal and enter > sudo apt-get update?
Does that work?

---

### Post by earl100 on 2011-12-06
Thanks for the quick atention.  I get an error msg, either when I use the launcher button and go to the software center and pick out a download, or if I use the terminal.

The error message says: "Check your internet connection."

My question is: How do I restore/refresh the apt-get application without using apt-get.

You see...if I use 
"apt-get update" I will get an error message, not an update.

---

### Post by earl100 on 2011-12-06
> **earl100 said:**
> Thanks for the quick atention.  I get an error msg, either when I use the launcher button and go to the software center and pick out a download, or if I use the terminal.

The error message says: "Check your internet connection."

My question is: How do I restore/refresh the apt-get application without using apt-get.

You see...if I use 
"apt-get update" I will get an error message, not an update.

So, can anyone help?  Any suggestions?

---

### Post by oldos2er on 2011-12-06
Please don't bump your post more than once in 24 hours.

Can you post the full terminal output of **sudo apt-get update** ?

---

### Post by phidia on 2011-12-06
earl100, do you know that your internet connection is working on the machine with this problem? Anyway it seem the package manager is unable to connect.

Anyway look at this [guide here]("http://askubuntu.com/questions/78849/ubuntu-software-center-check-your-internet-connection") and see if that will help you get apt working.

---

### Post by earl100 on 2011-12-08
No.

Read my question.

Once I have apt-get fixed/restored I'll comply with your request.

Thanks,

Earl

---

### Post by earl100 on 2011-12-08
> **phidia said:**
> earl100, do you know that your internet connection is working on the machine with this problem? Anyway it seem the package manager is unable to connect.

Anyway look at this [guide here]("http://askubuntu.com/questions/78849/ubuntu-software-center-check-your-internet-connection") and see if that will help you get apt working.

Read my question.  I can upload and download fine...you're reading this, right?

When i try to use apt-get,either in the console window, or the GUI, I get an error message.  Not to put too fine a point on it, but I'd like to repair or replace my apt-get program.

In fact, my question was, originally, can any one offer a suggestion?

Thanks,

Earl

---

### Post by westie457 on 2011-12-08
> **earl100 said:**
> No.

Read my question.

Once I have apt-get fixed/restored I'll comply with your request.

Thanks,

Earl

It looks like the srever you are trying to download from is having problems. Suggest you change to a different server. You can do it following these simple steps :-

1, Open the Software Center

2, Click on Edit and select Software Sources....

3, In the window that opens, look in the 'Ubuntu Software' tab for Download from: Click the box next to this and select Other...

4, Next you click on 'Select Best Server' and wait. After a few moments click on 'Choose Server'.

Exit out of the Software Center and open a terminal. Then type in sudo apt-get update. 

Any errors post the entire output here between [CODE] tags by clicking on # at the top of the message window.

Thank you.

---

### Post by earl100 on 2011-12-10
> **westie457 said:**
> It looks like the srever you are trying to download from is having problems. Suggest you change to a different server. You can do it following these simple steps :-

1, Open the Software Center

2, Click on Edit and select Software Sources....

3, In the window that opens, look in the 'Ubuntu Software' tab for Download from: Click the box next to this and select Other...

4, Next you click on 'Select Best Server' and wait. After a few moments click on 'Choose Server'.

Exit out of the Software Center and open a terminal. Then type in sudo apt-get update. 

Any errors post the entire output here between ```
 tags by clicking on # at the top of the message window.

Thank you.
Tried the 404 fix, and the search for a better server.
The search for a better server gave me, ultimately, an error message which said: "No suitable download server was found.  Check your internet connection."

I love being able to repeat myself, so ...My internet connection is fine.  A different drive with Ubuntu in the same machine uses apt-gets, and works just fine. just fine.

Other downloads from other sources works just fine.  Apt-get doesn't work.

Sudo apt-get update gets this at the end: [CODE]Fetched 468 B in 3s (127 B/s)
Reading package lists... Done
W: GPG error: http://us.archive.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://archive.canonical.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/Release  

W: Failed to fetch http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

I don't know how to paste something "between the #".

Given the above, could it be that something is wrong with my apt-get program?

Thanks for the attention.

---

### Post by oldos2er on 2011-12-11
"http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/oneiric/main/binary-i386/Packages" and "http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/oneiric/main/source/Sources" don't exist, there's only a Natty repo there, so I'd remove that from your sources.

To fix the BADSIG errors, run these commands one at a time: ```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
```

---

### Post by earl100 on 2011-12-15
Ann,

I entered:

sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update

in a terminal window, one line at a time. My apt-get is now restored, or repaired.

Don't know why I didn't think of it myself.

Thanks for the help.

Earl100

---

### Post by oldos2er on 2011-12-15
You're welcome. Can you please mark the thread as 'Solved' (under Thread Tools)? Thanks.

---

