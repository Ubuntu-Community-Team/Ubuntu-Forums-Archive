---
title: "Problems with CheckGmail today"
date: 2011-09-08
forum: General Help
---

### Post by birdmanuk on 2011-09-08
Hi,

  Anyone else having problems with CheckGmail? When launched, I get a dialog box asking for id and password, but it doesn't ever accept / connect.

I'm at the latest version, this happens on both of my laptops.

cheers

---

### Post by dbdexter on 2011-09-08
in the username field you must type in your mail without "@gmail.com". Example
"king80@gmail.com" becomes "king80"
It worked for me at first attempt. ):P;)

---

### Post by birdmanuk on 2011-09-08
OK, I've been using this app for years, so it's only the last few days that it has been failing. I need to now work out if it's Gmail or Ubuntu that is the problem. I'm running 10.10, maybe it was an update that went on in the last couple of days. I'm surprised I'm the only one having the problem.

cheers

---

### Post by ajgreeny on 2011-09-08
Just out of interest, try gmail-notify from the repos which is very similar to your app, I think.  That could rule out gmail problems, if nothing else, and you can uninstall it afterwards if you want to..

---

### Post by Absorbed on 2011-09-08
I've been having the same problem with checkgmail for the last day or two. 
I can login via the web no problem. Removing @gmail.com" in checkgmail didn't work for me.

---

### Post by birdmanuk on 2011-09-08
Ah, good, I'm not alone. I have tried a few other clients as suggested, all of which work.

---

### Post by Absorbed on 2011-09-08
Rather strangely, the problem appears to have fixed itself, unless there was an update that I missed.

Edit: It's now unfixed itself.

---

### Post by arvs on 2011-09-08
I have the same problem since a few days, and updating to the latest version didn't help.

In a different thread someone suggested to use the -no_cookies flag, which indeed works for me, but the use of the program is more limited this way.

---

### Post by birdmanuk on 2011-09-10
This thread has others seeing the same problem - [http://ubuntuforums.org/showthread.php?t=1632402&highlight=checkgmail](http://ubuntuforums.org/showthread.php?t=1632402&highlight=checkgmail)

checkgmail -no_cookies works, but limited function.

Sadly not fixed :-)

---

### Post by solitaire on 2011-09-10
Think Google's been playing around with the Authentication for Gmail this week!
The "googsystray" app hasn't worked for me for the past few days...

---

### Post by gdesilva on 2011-09-11
I noticed that the problem started after running Ubuntu updates but as someone mentioned earlier it may also be something to do with Gmail updates.

No problems with Gmail-notify but the problem is I cannot get my audio file played when new mail arrives!

I sent an email to the Checkgmail project leader but have not heard anything back from him.


EDIT no_cookies option works for me.

---

### Post by gdesilva on 2011-09-11
A fix has been made available by Jan Jergus - thanks Jan.

[https://sourceforge.net/tracker/?func=detail&aid=3406322&group_id=137480&atid=738663](https://sourceforge.net/tracker/?func=detail&aid=3406322&group_id=137480&atid=738663)

What is needed to do is to download the patch written by Jan [https://sourceforge.net/tracker/download.php?group_id=137480&atid=738663&file_id=423104&aid=3406322](https://sourceforge.net/tracker/download.php?group_id=137480&atid=738663&file_id=423104&aid=3406322)

Then go to the directory where the downloaded patch is and run

sudo patch /usr/bin/checkgmail checkgmail.patch

You may want to read Jan's comments about the solution first but it does work for me.

Hope this is helpful.

---

### Post by mrphoenix on 2011-09-16
"Error: Incorrect username or password" again now...

Please help!:(

---

### Post by gdesilva on 2011-09-18
mrphoenix, I presume you applied the patch and it was working for some time and now it has stopped working again? If that is the case, did you by any chance re-install Checkgmail as this requires applying the patch once again. Since I applied the patch a few days ago, Checkgmail has been working fine, even just a few minutes ago. Sorry cannot be of more help.


EDIT : tried the patch once again on another computer and it all works good for me. Not sure what your problem could be.....

---

### Post by LRY on 2011-09-19
The patch fixes the problems with logging in.  Thanks!

LRY

---

### Post by ivanhelguera on 2011-09-20
Works for me  - Thanks!
maybe it should me marked as solved?

---

### Post by blueswerks on 2011-09-21
Patch worked for me, too.

Thanks!

---

### Post by mustang on 2011-12-29
> **gdesilva said:**
> A fix has been made available by Jan Jergus - thanks Jan.

[https://sourceforge.net/tracker/?func=detail&aid=3406322&group_id=137480&atid=738663](https://sourceforge.net/tracker/?func=detail&aid=3406322&group_id=137480&atid=738663)

What is needed to do is to download the patch written by Jan [https://sourceforge.net/tracker/download.php?group_id=137480&atid=738663&file_id=423104&aid=3406322](https://sourceforge.net/tracker/download.php?group_id=137480&atid=738663&file_id=423104&aid=3406322)

Then go to the directory where the downloaded patch is and run

sudo patch /usr/bin/checkgmail checkgmail.patch

You may want to read Jan's comments about the solution first but it does work for me.

Hope this is helpful.

Thank you!

---

