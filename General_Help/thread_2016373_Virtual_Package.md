---
title: "Virtual Package"
date: 2012-07-04
forum: General Help
---

### Post by gabmuks on 2012-07-04
Hello and good day to all.

I have Ubuntu 12.04 and have been using Google Chrome successfully
for months. It works faster on my computer than Firefox or Chromium
and Flash-player doesn't crash with Chrome.

Yesterday after installing updates from Update Manager, the Chrome
browser could not be opened. I had to use Chromium to access net.

With the help of Moderator Ubudog I tried to un-install Chrome.

This was the response...[ATTACH]220653[/ATTACH]

Does anyone know how to uninstall a virtual package?
Or is there another way fix this problem?

Would it be better to just re-install Ubuntu 12.04?

Thank you for your time

Best regards

Pat L.

---

### Post by dino99 on 2012-07-04
open nautilus to search "google-chrome", select the package(s) to remove & right-click on it to check the property (address)

then you can erase the package(s) via:  sudo rm /path 2 that package

---

### Post by adit on 2012-07-04
How did you install google-chrome?
google-chrome is not in the official ubuntu repositories.
Which repository did you use to install google-chrome?
Did you install by a dowloaded .deb file?

---

### Post by vasa1 on 2012-07-04
You could try ```
sudo apt-get purge google-chrome-stable
```

I know that that is what Chrome is called for me because after running
```
dpkg --get-selections > ~/Desktop/installed-software
```
and opening the file "installed-software", I see that it is not **google-chrome** but **google-chrome-stable**.

---

### Post by vasa1 on 2012-07-04
> **adit said:**
> How did you install google-chrome?
google-chrome is not in the official ubuntu repositories.
Which repository did you use to install google-chrome?
Did you install by a dowloaded .deb file?

[http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/)

But this page has a lot more information: [http://dev.chromium.org/getting-involved/dev-channel](http://dev.chromium.org/getting-involved/dev-channel)

---

### Post by vasa1 on 2012-07-04
> **gabmuks said:**
> ...
Yesterday after installing updates from Update Manager, the Chrome
browser could not be opened. I had to use Chromium to access net.
...

It's possible you have run into this bug: [https://code.google.com/p/chromium/issues/detail?id=134940](https://code.google.com/p/chromium/issues/detail?id=134940)

There's a help group here: [http://productforums.google.com/forum/#!category-topic/chrome/linux/UVGRyv50t0E](http://productforums.google.com/forum/#!category-topic/chrome/linux/UVGRyv50t0E)

Basically, if your CPU is unsupported (polite speak for oldish), the new Pepper Flash, **if enabled**, won't let Chrome version 20 start. I'm assuming you have been updated to Chrome 20.

So if you just want to run Chrome 20 **without using Flash**, you should be able to do so by opening a terminal and typing
```
google-chrome --disable-bundled-ppapi-flash
```

Chrome should then run and use another Flash plug-in, if available.

You will know by checking out YouTube.

If Flash still doesn't work with Chrome, then, **if** you have Firefox installed and **if** Flash works satisfactorily, you could use the Flash plug-in that Firefox uses like this:

After starting Chrome, type **about : plugins** (without any spaces) in Chrome's address bar and hit enter.
Then, on the page that opens, click on the little plus sign near the top right of the page to show details.

Make sure that the **first** Flash plug-in is **disabled** and that the **second** Flash plug-in is **enabled**. (The image has the opposite because Pepper Flash works for me.)

---

### Post by vasa1 on 2012-07-04
I forgot to mention that the bug I linked to shows that Google have started to work on a fix. Fingers crossed.

---

### Post by gabmuks on 2012-07-04
> **vasa1 said:**
> You could try ```
sudo apt-get purge google-chrome-stable
```

I know that that is what Chrome is called for me because after running
```
dpkg --get-selections > ~/Desktop/installed-software
```
and opening the file "installed-software", I see that it is not **google-chrome** but **google-chrome-stable**.

Thank you all for kind replies.

Here is snapshot....[ATTACH]220661[/ATTACH]

Another strange thing is that I have two computers both with Chrome browser. Right now I am using the older 2003 model computer and Chrome still works fine. Both computers use Ubuntu 12.04 and it works great.

---

### Post by gabmuks on 2012-07-04
Hello and thank you for kind replies.

I did manage to uninstall the google-chrome-stable from
both of my computers using the commands that you have helped me with.

I then re-installed chrome to both computers.

The old 2003 computer is still able to use the Chrome browser
with no problems.


But my newer computer has same problem even with new installation
of Chrome. 

So something installed by the update manager must be stopping
the Chrome from loading.

---

### Post by gabmuks on 2012-07-04
Hello and good day.

There is one difference that I know of between the old and new
computer. I have different repositories listed on each computer.

The newer computer has more repositories listed.
One or more of them may have added something faulty to my computer.

Can anyone tell me how to find and change the repositories in Ubuntu 12.04?

I can compare the repositories on each computer and delete the ones that may be causing problems.

Thank you for your time.


Best regards

Pat L.

---

### Post by gabmuks on 2012-07-04
[ATTACH]220681[/ATTACH]

[ATTACH]220682[/ATTACH]

I found my repositories.

Do any of these repositories look suspicious?

---

### Post by vasa1 on 2012-07-04
> **gabmuks said:**
> ...
Another strange thing is that I have two computers both with Chrome browser. Right now I am using the older 2003 model computer and Chrome still works fine. Both computers use Ubuntu 12.04 and it works great.

Type **about:version** in the address bar for the Chrome browser that works and hit enter. Then post the information here.

For the Chrome browser that doesn't work, see if you have a folder like this:
/home/your_name/.config/google-chrome. If you do, look for a file called **Local State**. (Yes, there's a space in there.) Open it with your text editor or however you wish and look near the bottom for something like "stats_version": "20.0.1132.47" and paste that line here.

Alternatively, open a terminal and just type:
```
google-chrome --version
```
(No need of "stable")

As far as repositories go, I don't know how necessary **medibuntu** is nowadays. The **xswat** one is for specialised needs and should not normally be found on a computer running Ubuntu that has not given problems.

My suggestion is that you can just **untick** them to **disable** them. That way, you can regain them if you choose by ticking them again. In any case, you can untick any repo that has "source" in it unless you examine source code.

By the way, could you please mention whether you are the sole user of the computer or are others allowed to use it and install software on it?

---

### Post by vasa1 on 2012-07-04
By the way, why do you have **Custom Server**? How did it get there?

---

### Post by vasa1 on 2012-07-04
> **gabmuks said:**
> Hello and thank you for kind replies.

I did manage to uninstall the google-chrome-stable from
both of my computers using the commands that you have helped me with.

I then re-installed chrome to both computers.

The old 2003 computer is still able to use the Chrome browser
with no problems.


But my newer computer has same problem even with new installation
of Chrome. 

So something installed by the update manager must be stopping
the Chrome from loading.

On the newer computer, switch Chrome off and check that no Chrome process is running. Then rename ```
/home/user-name/.config/google-chrome
```to something else. Now see if Chrome works. If it does, you won't have any of your old bookmarks, extensions and history, but that's for later.

---

### Post by gabmuks on 2012-07-05
Sorry for delay....

internet was down this morning.

Att DSL would not allow me access to net
unless I had Windows and Internet Explorer.
They said my modem password did not match theirs.
I had to call ATT to get back online.


Anyway here is snapshot...[ATTACH]220726[/ATTACH]

---

### Post by gabmuks on 2012-07-05
> **vasa1 said:**
> Type **about:version** in the address bar for the Chrome browser that works and hit enter. Then post the information here.

For the Chrome browser that doesn't work, see if you have a folder like this:
/home/your_name/.config/google-chrome. If you do, look for a file called **Local State**. (Yes, there's a space in there.) Open it with your text editor or however you wish and look near the bottom for something like "stats_version": "20.0.1132.47" and paste that line here.

Alternatively, open a terminal and just type:
```
google-chrome --version
```
(No need of "stable")

As far as repositories go, I don't know how necessary **medibuntu** is nowadays. The **xswat** one is for specialised needs and should not normally be found on a computer running Ubuntu that has not given problems.

My suggestion is that you can just **untick** them to **disable** them. That way, you can regain them if you choose by ticking them again. In any case, you can untick any repo that has "source" in it unless you examine source code.

By the way, could you please mention whether you are the sole user of the computer or are others allowed to use it and install software on it?

Here is Chrome version..[ATTACH]220727[/ATTACH]

Thank you for your reply and all of your help.
I am the sole user of this computer. No one else
has ever used it for anything. I have been on other
websites that had Ubuntu programs like conty and
I probably unknowingly downloaded and added repositories
that I shouldn't have.

I will try to un-tick medbuntu and the other that you mentioned.

Also, I don't know anything about "custom server".
What is that for?

Thank you for your time

Best regards

Pat L.

---

### Post by gabmuks on 2012-07-05
I have un-ticked Medbuntu and xswat.


Here are software providers listed...[ATTACH]220728[/ATTACH]

---

### Post by gabmuks on 2012-07-05
> **vasa1 said:**
> On the newer computer, switch Chrome off and check that no Chrome process is running. Then rename ```
/home/user-name/.config/google-chrome
```to something else. Now see if Chrome works. If it does, you won't have any of your old bookmarks, extensions and history, but that's for later.

Here is results...[ATTACH]220729[/ATTACH]


Sorry sir, but I'm not sure what it is that I should re-name. (or how)

---

### Post by gabmuks on 2012-07-05
Something interesting...
Ubuntu Software Center says Chrome is installed.

But my repository list on the this machine does not include
the google chrome repository.

But on my older machine with working Chrome,
the repository is listed.

I tried to add the repository manually.
But it was not allowed.

[ATTACH]220730[/ATTACH]

---

### Post by gabmuks on 2012-07-05
Thank you for kind reply.

You are absolutely correct!!

The bug was mentioned earlier in this thread,
but I got so involved with my replies that I failed to checkout
the bug.

Chrome is now working after getting rid of the pepperflash.


I am grateful for the help that you all have provided.
As always, you have all taught me much.
And saved me again!

And I thank you for your time.

Best regards

Pat L.

---

### Post by gabmuks on 2012-07-07
Thank you all.

The bug fix that you posted allowed Google Chrome to load.


So I will close this thread.

Thank you for kind replies and knowledge.

Best regards
Pat L.

---

