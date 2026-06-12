---
title: "Chrome GMail Webapp as Default Email Client"
date: 2010-05-19
forum: General Help
---

### Post by megamanexent on 2010-05-19
Many of you probably already know this, but the Gmail web Client can be set as the default Email client using Prism or Chrome. All you have to do is create a script file in your home directory and place this into there. (this is for Chrome by the way)

```
#!/bin/sh

/opt/google/chrome/google-chrome --app="[https://mail.google.com/mail?view](https://mail.google.com/mail?view)=cm&tf=0&to=`echo $1 | sed 's/mailto://'`"
```Make the script executable, (right click on file-->Properties-->Permissions-->check box or navigate to directory and chmod +x the file)

This is great, however, I noticed that when you add that script as the default mail client, gm-notify insist on bringing you to the compose message dialog(when gm-notify is set to open the current mail client) instead of the inbox, so i changed your script to weed that little bug out!

```
#!/bin/sh
if ($1 > /dev/null); then
/opt/google/chrome/google-chrome --app="https://mail.google.com/mail/?hl=en&shva=1"
else
/opt/google/chrome/google-chrome --app="https://mail.google.com/mail?view=cm&tf=0&to=`echo $1 | sed 's/mailto://'`"
fi
```So now we have the best of both worlds, opening from gm-notify gives me the inbox, while clicking on an email address gives me the compose message dialog. 

Thanks to this video for the idea: [http://www.youtube.com/watch?v=WGv9kwwya-w](http://www.youtube.com/watch?v=WGv9kwwya-w)

I hope this helps someone! Also, the script can easily be rewritten for Firefox.

```
#!/bin/sh
if ($1 > /dev/null); then
firefox "https://mail.google.com/mail/?hl=en&shva=1"
else
firefox "https://mail.google.com/mail?view=cm&tf=0&to=`echo $1 | sed 's/mailto://'`"
fi
```

Please give any corrections to the script if needed. Thanks!

---

### Post by SlidingHorn on 2010-05-19
Cool idea...see if you can get this moved over to the tutorials section

---

### Post by megamanexent on 2010-05-19
I do not want to create a duplicate thread, how do i submit this one to tutorials and tips, sorry for the noob question?

* Update *

Never-mind i submitted the post again, now just have to wait and see!

---

### Post by c089 on 2011-03-04
Hey, thanks for the great script - one suggestion though, the way you check for an empty string will try to execute the argument, so if you would try and send an email to 'rm -rf /home/youruser' or something like that... Well, just check like this instead:
```
if [ -z $1 ]; then
```

---

### Post by megamanexent on 2011-03-05
> **c089 said:**
> Hey, thanks for the great script - one suggestion though, the way you check for an empty string will try to execute the argument, so if you would try and send an email to 'rm -rf /home/youruser' or something like that... Well, just check like this instead:
```
if [ -z $1 ]; then
```


Woahh, Thank you. Major flaw :o
I also will have to change [this thread]("http://ubuntuforums.org/showthread.php?t=1488068") to!!

---

