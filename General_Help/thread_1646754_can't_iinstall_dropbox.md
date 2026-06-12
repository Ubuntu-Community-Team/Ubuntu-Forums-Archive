---
title: "can't iinstall dropbox"
date: 2010-12-16
forum: General Help
---

### Post by beacon on 2010-12-16
I have just installed ubuntu 10.10 on a friend's computer, but I am unable to download and install dropbox. Every thread I have consulted mentions that it is available in the repositories.  I am unable to find it in either Synaptic or software centre. When I try to download it from dropbox directly I continually get the message that it cannot be downloaded because an unknown error occurred. 

Please can anyone advise?

---

### Post by tajiknomi on 2010-12-16
> **beacon said:**
> I have just installed ubuntu 10.10 on a friend's computer, but I am unable to download and install dropbox. Every thread I have consulted mentions that it is available in the repositories.  I am unable to find it in either Synaptic or software centre. When I try to download it from dropbox directly I continually get the message that it cannot be downloaded because an unknown error occurred. 

Please can anyone advise?

[SIZE=2]I don't know why you are getting this Error, but you try this >[/SIZE][http://dl.dropbox.com/u/16158781/nautilus-dropbox_0.6.4_i386.deb](http://dl.dropbox.com/u/16158781/nautilus-dropbox_0.6.4_i386.deb)

[SIZE=2]Edit:-The [/SIZE][SIZE=2]repository[/SIZE][SIZE=2] will ***automatically*** added,once you had installed it,You can Add repository ***manually*** too ,Check it out here > [/SIZE][https://www.dropbox.com/downloading](https://www.dropbox.com/downloading)

---

### Post by beacon on 2010-12-16
Thank you for the reply. The link you provided is precisely the one I have been using and which always gives me the same message: /tmp/nautilus-dropbox_0.6.4_i386-7.deb could not be opened, because an unknown error occurred.


It doesn't help that Dropbox will be automatically added to the repository when installed if I can't install it in the first place. I really don't know what is wrong.

---

### Post by tajiknomi on 2010-12-16
[SIZE=2]I am not sure, but its seems like Something mess with your Gdebian-manager, thats why this gives you an Unknown Error,

I had recently read somewhere that mavrick uses ***software-center*** for Opening debian-packages by Default, try opening dropbox with **Gdebian-package manager**,...right click a .deb file(Dropbox in this Case), select "Properties", go to the "Open With" tab  and select "GDebi Package Installer" instead of "Ubuntu Software Center"[/SIZE]
[SIZE=2]If it is not their, then you must has to install it by this COde:-
[/SIZE]```
sudo apt-get install gdebi gdebi-core
```
[SIZE=2] 
[/SIZE]

---

### Post by beacon on 2010-12-16
Thanks once again. That looks promising. I have checked and Gdebian package manager is said to be already installed. However, it does not appear in the list when I tick 'open with'. I added it to custom command, but nothing happened.

The synaptic list shows a red circular icon beside Gdebian, but i don't know what that means. Perhaps you can help.

I appreciate it.

---

### Post by tajiknomi on 2010-12-17
[SIZE=2]Have you tried other packages..? Is they are installing perfectly...?

Add Drop-box to your Repository using this Command:-

[/SIZE]```
[SIZE=3]sudo apt-get update;sudo apt-get upgrade nautilus-dropbox[/SIZE]
```

[SIZE=2]For  authenticated Drop-box repositories,run:-

[/SIZE]```
sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 5044912E
```

---

### Post by matt_symes on 2010-12-17
Hi

Download dropbox from the link given in the previous post, but save to your download folder instead of opening with gDebi.

Open a terminal and navigate to your downloads folder and type 

```
sudo dpkg -i nautilus-dropbox_0.6.4_i386.deb
```This should install it on your machine.

And thanks. You reminded me to reinstall dropbox. :)

EDIT:

As  tajiknomi pointed out it's also in the repros (Cheers, i did not  know that), but the command has a slight typo and should be....

```
sudo apt-get update && sudo apt-get install nautilus-dropbox
```Kind regards

---

### Post by beacon on 2010-12-17
Many thanks to both of you, tajiknomi and matt_symes. I wouldn't be able to tell you what worked, but a combination of your ideas and suggestions seems to have done the trick. I am very grateful.

---

### Post by MJae on 2010-12-27
> **matt_symes said:**
> Hi

Download dropbox from the link given in the previous post, but save to your download folder instead of opening with gDebi.

Open a terminal and navigate to your downloads folder and type 

```
sudo dpkg -i nautilus-dropbox_0.6.4_i386.deb
```This should install it on your machine.

And thanks. You reminded me to reinstall dropbox. :)

EDIT:

As  tajiknomi pointed out it's also in the repros (Cheers, i did not  know that), but the command has a slight typo and should be....

```
sudo apt-get update && sudo apt-get install nautilus-dropbox
```Kind regards


Apparently, it's been over a year since I visited (June 30, 2009).

But that's not the reason I came here.

I've been having the same problem. The instructions above are what I did but it doesn't work for me. System tells me something about windows and such. I forgot the exact error message. I guess, I'ma have to try again to get a proper answer to my problem.

---

### Post by matt_symes on 2010-12-27
Hi

> I've been having the same problem. The instructions above are what I did but it doesn't work for me. System tells me something about windows and such. I forgot the exact error message. I guess, I'ma have to try again to get a proper answer to my problem.

Try again but post the whole output back on this thread. That way we will know the error message.

Kind regards

---

### Post by Ceiber Boy on 2010-12-27
Thanks for this thread, I've found it helpful

---

