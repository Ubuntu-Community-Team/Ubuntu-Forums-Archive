---
title: "E: Could not get lock /var/lib/dpkg/lock"
date: 2011-07-01
forum: General Help
---

### Post by louisgonick on 2011-07-01
So I was downloading some stuff through the pacakage manager, then I tried to download some other stuff on terminal and I get this E: Could not get lock /var/lib/dpkg/lock. 

Any suggestions?

---

### Post by oldos2er on 2011-07-01
Only one instance of a package manager (Software Center, Synaptic, or apt-get) can be running at any given time.

---

### Post by sam_delta on 2011-07-01
you can only have one process downloading/installing/updating at a time, just wait until the first process finish to put the second one.

you can also tell apt-get to install multiple files at once as follows
```
 sudo apt-get install app1 app2 app3 ...
```

if your not currently installing/updating anything and you still get that error, try rebooting the pc.

sam

---

### Post by louisgonick on 2011-07-01
> **sam_delta said:**
> you can only have one process downloading/installing/updating at a time, just wait until the first process finish to put the second one.

you can also tell apt-get to install multiple files at once as follows
```
 sudo apt-get install app1 app2 app3 ...
```if your not currently installing/updating anything and you still get that error, try rebooting the pc.

sam

I am downloading something through software center... does that count also???

---

### Post by sam_delta on 2011-07-01
yes, wait until it finishes installing. software center uses apt-get to install the software.

sam

---

### Post by louisgonick on 2011-07-01
> **sam_delta said:**
> yes, wait until it finishes installing. software center uses apt-get to install the software.

sam

the problem got fixed temporally... now when I try to download from software center I get this error message: 

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.
 
heres a screen shot :[[IMG]http://s3.postimage.org/1nrx6m5qc/Screenshot.jpg[/IMG]]("http://postimage.org/image/1nrx6m5qc/")

---

### Post by oldos2er on 2011-07-01
Try ```
sudo apt-get update && sudo apt-get install ttf-mscorefonts-installer
```

---

### Post by louisgonick on 2011-07-01
> **oldos2er said:**
> Try ```
sudo apt-get update && sudo apt-get install ttf-mscorefonts-installer
```

I get to a part in with some license agreements and I cant press ok

---

### Post by nitstorm on 2011-07-01
You gotta move around with the arrow keys and click enter to proceed.

---

### Post by louisgonick on 2011-07-01
> **nitstorm said:**
> You gotta move around with the arrow keys and click enter to proceed.
Enter does not work

---

### Post by nitstorm on 2011-07-01
> **louisgonick said:**
> Enter does not work

Make sure the Accept or okay button is highlighted or selected when you hit enter. Or try hitting Space too.

---

### Post by louisgonick on 2011-07-01
> **nitstorm said:**
> Make sure the Accept or okay button is highlighted or selected when you hit enter. Or try hitting Space too.

I tried again and I get this: ```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by nitstorm on 2011-07-01
> I tried again and I get this:
Code:
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Run one process at a time. Either Ubuntu Software Center, Synaptic Manager or the terminal install. Please do not run more than one of these applications at any given time. If you do, you will keep running into this issue everytime you keep doing so.

---

### Post by louisgonick on 2011-07-01
> **nitstorm said:**
> Run one process at a time. Either Ubuntu Software Center, Synaptic Manager or the terminal install. Please do not run more than one of these applications at any given time. If you do, you will keep running into this issue everytime you keep doing so.

None of them are running. Just to check can u give the the names of the proceses to close them on system monitor?

---

### Post by louisgonick on 2011-07-01
I get this when  I try to open synaptic package manager :[[IMG]http://s1.postimage.org/2o4i42b9g/Screenshot_1.jpg[/IMG]]("http://postimage.org/image/2o4i42b9g/")[IMG]http://postimage.org/image/2o4i42b9g/[/IMG]

---

### Post by sam_delta on 2011-07-01
try rebooting. When facing the licence, try pressing the 'tab' button to get the ok highlighted, if not, try navigating with tab, arrow keys, enter and spacebar.

sam

---

### Post by louisgonick on 2011-07-01
> **sam_delta said:**
> try rebooting. When facing the licence, try pressing the 'tab' button to get the ok highlighted, if not, try navigating with tab, arrow keys, enter and spacebar.

sam

I will try rebooting, I also got some error messages when I tried to download some updates, I guess it might be related to this

---

### Post by nitstorm on 2011-07-01
Close the terminal that you are using to install the package first with this command: (this also applies to all terminals that might be used to update packages or install something new either from the network or not)
```
exit
```

Then check if you are running the software center or the update-manager. Not sure what Software Center's process name would be(softwarecenter probably???) , but I am a little confident that update-manager's process name is update-manager. (Not sure though)

Then try to install the package you are trying to install using a fresh terminal. Even if that doesn't work, log out and log back in and try installing (without running the software-center or update-manager)  That should hopefully do the trick.


*A little late on the typing but still going to let it be..*

---

### Post by shri19 on 2011-07-01
It should, make sure to move you choice to OK( or "YES" or something) button using the arrow keys and press enter. I did this installation a few days back.

---

### Post by louisgonick on 2011-07-01
after I rebooted I tried again and got this ```
N: Ignoring file 'medibuntu.lis' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
W: GPG error: http://packages.medibuntu.org natty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```

I am a total noob but wouldn't using recovery mode help??

---

### Post by sam_delta on 2011-07-01
your fine in normal mode, do as it says, run 
```
 sudo dpkg --configure -a 
```

dont worry, let us know how it goes
sam

---

### Post by louisgonick on 2011-07-01
> **sam_delta said:**
> your fine in normal mode, do as it says, run 
```
 sudo dpkg --configure -a 
```dont worry, let us know how it goes
sam

it worked now but at the end I get this ```
All done, no errors.
All fonts downloaded and installed.
Updating fontconfig cache for /usr/share/fonts/truetype/msttcorefonts
N: Ignoring file 'medibuntu.lis' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

```

---

### Post by nitstorm on 2011-07-01
```
cp /etc/apt/sources.list.d/medibuntu.lis /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by sam_delta on 2011-07-01
try this.
```
 sudo mv /etc/apt/sources.list.d/medibuntu.lis /etc/apt/sources.list.d/medibuntu.list
```

for some reason, medibuntu repos file is mising the last 't' in its name "medibuntu.list"
you should not get that error again after running this command

sam

---

### Post by louisgonick on 2011-07-01
> **sam_delta said:**
> try this.
```
 sudo mv /etc/apt/sources.list.d/medibuntu.lis /etc/apt/sources.list.d/medibuntu.list
```for some reason, medibuntu repos file is mising the last 't' in its name "medibuntu.list"
you should not get that error again after running this command

sam
I typed in this:

sudo dpkg --configure -a
and aparently the problem is fixed because I just downloaded a random app from the appstore. This whole issue made me really miss the way software is installed on windows... I'll be back I the issue is back

---

### Post by nitstorm on 2011-07-01
The problem has been resolved, so please mark the thread solved.

---

### Post by sam_delta on 2011-07-01
Alright, now that everything is working fine, you will find even easier to install apps in ubuntu.

Every app, for free, comming from a safe place (repos) just a click away. You cant beat that.

have fun
sam

---

