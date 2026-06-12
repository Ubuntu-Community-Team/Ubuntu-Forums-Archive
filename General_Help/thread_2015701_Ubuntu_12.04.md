---
title: "Ubuntu 12.04"
date: 2012-07-03
forum: General Help
---

### Post by gabmuks on 2012-07-03
Hello and good day to all

Today I was installing the updates from package manager as usual.

After the updating was complete, my Chrome browser would not load.

I have re-installed Google Chrome numerous times today.
But it still will not load the Chrome browser.
I had to install the Chromium browser to get onto the net.

I have two computers going. One still has a working Chrome browser.

Does anyone know what update might have caused Chrome to disable?
Does anyone know how to fix?

I tried to report on Lauchpad, but they have made it too difficult to report a bug. It used to be easy.

Thank you for your time.

Best regards

Pat L.

---

### Post by flipper T on 2012-07-03
hi

try opening chrome from a terminal & post output here.

---

### Post by gabmuks on 2012-07-03
Thank you

I will try to open from terminal if you can tell me how to do it.

---

### Post by gabmuks on 2012-07-03
I know how to open terminal.
But I do not know command to open Chrome from terminal.

---

### Post by gabmuks on 2012-07-03
I did try to type in "chrome" in the terminal.

But response is "command not found".

---

### Post by flipper T on 2012-07-03
type ¨google-chrome¨ & press enter :)

---

### Post by gabmuks on 2012-07-03
[ATTACH]220621[/ATTACH]Thank you for reply.

I typed in google-chrome.

Then I hit "enter".

The cursor moved to the next line...blinked a few times...then
just stayed there. Nothing else happened.

> 

---

### Post by flipper T on 2012-07-03
you have chromium successfully installed ?

use chromium then ?

ps how did you install chrome ?

---

### Post by gabmuks on 2012-07-03
Thank you for reply.

I installed it through "Ubuntu Software Center".

I used to use Chromium but it is very slow and Flashplayer
crashes constantly. Chrome works great. This is the first time
I have had any trouble with Chrome.
They did something with the Ubuntu updates that made it stop working. I don't understand why.

 Do you know of anyone who could help with this problem?

---

### Post by flipper T on 2012-07-03
go to your home directory and go to .config (you will have to choose the option to see hidden folders)

in there should be a google-chrome folder.

delete this & then try to launch chrome.

---

### Post by ubudog on 2012-07-03
> **flipper T said:**
> go to your home directory and go to .config (you will have to choose the option to see hidden folders)

in there should be a google-chrome folder.

delete this & then try to launch chrome.

+1

Note that that will delete your bookmarks too, so you can do:
```
cp ~/.config/google-chrome/Default/bookmarks ~/bookmarksbak
```

That will backup your bookmarks.

Then, delete the google-chrome directory and fire up Chrome.

Chrome should make a new .google-chrome.  To copy your bookmarks back into place:
```
cp ~/bookmarksbak ~/.config/google-chrome/Default/
```

That would also delete your extensions, history, and other stuff, so you could alternatively just backup the whole google-chrome directory and copy back the stuff you wish to restore once Chrome generates a new google-chrome directory.

Best, 
ubudog

---

### Post by gabmuks on 2012-07-03
Thank you for reply.

I went to .config and deleted the google-chrome file
then tried to load Chrome from terminal.

The response was the same.

Cursor moves to next line and stops.

---

### Post by ubudog on 2012-07-03
Hmm... run the following:
```
killall google-chrome && google-chrome
```

---

### Post by flipper T on 2012-07-03
hmm...indeed

getting late, so i´m out.

goodnight & goodluck

ps interesting username gabmuks, especially in reverse.

---

### Post by gabmuks on 2012-07-03
[ATTACH]220623[/ATTACH]

Thank you for reply.
Here is results...

---

### Post by ubudog on 2012-07-03
Could you try uninstalling it, and installing it from [Google's page]("https://www.google.com/intl/en/chrome/browser/")?

To uninstall:
```
sudo apt-get purge google-chrome
```

---

### Post by gabmuks on 2012-07-04
[ATTACH]220645[/ATTACH]

Thank you for reply.

Here is response from purge command....

---

### Post by ubudog on 2012-07-04
Try removing it from the Software Center.

Best,
ubudog

---

### Post by gabmuks on 2012-07-04
Thank you for reply

At Software Center, the only option

given for Chrome is to "re-install"

---

### Post by ubudog on 2012-07-05
> **gabmuks said:**
> Thank you for reply

At Software Center, the only option

given for Chrome is to "re-install"

Try this:
```
sudo apt-get remove google-chrome-stable
```

---

### Post by haresear on 2012-07-05
It sounds like you have run into the Flash/Chrome bug introduced with a recent Chrome update:
[http://ubuntuforums.org/showthread.php?t=2011882]("http://ubuntuforums.org/showthread.php?t=2011882")

and:
[http://ubuntuforums.org/showthread.php?t=2012659]("http://ubuntuforums.org/showthread.php?t=2012659")

---

### Post by gabmuks on 2012-07-05
> **haresear said:**
> It sounds like you have run into the Flash/Chrome bug introduced with a recent Chrome update:
[http://ubuntuforums.org/showthread.php?t=2011882]("http://ubuntuforums.org/showthread.php?t=2011882")

and:
[http://ubuntuforums.org/showthread.php?t=2012659]("http://ubuntuforums.org/showthread.php?t=2012659")

Thank you for kind reply.

You are absolutely correct!!

The bug was mentioned earlier in this thread,
but I got so involved with my replies that I failed to checkout
the bug.

Chrome is now working after getting rid of the pepperflash.


I am grateful for the help that you all have provided.
You have saved me again!

And I thank you for your time.

Best regards

Pat L.

---

