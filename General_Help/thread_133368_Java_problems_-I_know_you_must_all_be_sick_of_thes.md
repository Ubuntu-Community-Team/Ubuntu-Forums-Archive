---
title: "Java problems -I know you must all be sick of these."
date: 2006-02-20
forum: General Help
---

### Post by Darkness3477 on 2006-02-20
HI all, I've installed Ubuntu 5.10 today for the second time (Wiped it off so I could try another OS), and I'm just trying to install java. 

I've downloaded what I beleive to be the right thing, cd'ed to the directory where the downloaded file is and done everything that the ubuntu wiki.
I get to the last part of it where I must enter these lines into the terminal >   fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin
  sudo dpkg -i sun-j2re1.5_1.5.0+update06_i386.deb
after doing so I get this error message
> /home/darkness/jre-1_5_0_06-linux-i586.bin: line 1: syntax error near unexpected token `<'
/home/darkness/jre-1_5_0_06-linux-i586.bin: line 1: `<HTML><HEAD><TITLE>Error</TITLE></HEAD><BODY>'

WARNING: The package installation script exited with an error
value. Usually, this means, that the installation failed for some
reason. But in some cases there is no problem and you can continue
creating the Debian package.

Please check if there are any error messages. Press [Return] to
continue or Ctrl-C to abort.

Before that, it just tells me it is about to extract it....  After I get that message, I click enter and get this one;
> Testing extracted archive...
Invalid size (1 MB) of extracted archive. Probably you have not
enough free disc space in the temporary directory. Note: You can
specify an alternate directory by setting the environment variable
TMPDIR.


Aborted.

Removing temporary directory: done


Well, there you have it. My problem with Java. As it says down the bottom, there is not enough free disc space in the temp dir. Yet, I'm not sure how to fix it, or change dir's. So, if someone could help me, I'd be very helpful.

Thankyou and goodbye, Michael.

---

### Post by ajgreeny on 2006-02-20
Why do it the hard way?  Why not use synaptic or just apt get sun java from the repositories.  It worked for me without a problem.  Not sure about the temp space problem, but this did not seem to be a difficulty for me so it should be worth a try this simple way.

---

### Post by Darkness3477 on 2006-02-20
Hmm. I will do that. I never remembered seeing I could get Sun Java from the Repositories. What would I type in? Just apt-get install java?

---

### Post by kaamos on 2006-02-20
Hello!

Look here: [http://ubuntuforums.org/showthread.php?t=81577](http://ubuntuforums.org/showthread.php?t=81577)

---

### Post by Darkness3477 on 2006-02-20
Woah. Thanks! Now I can get started on some homework, and then to my game.

As a side note, what IDE do you recomend for someone who wants to get into Java programming?

---

### Post by arsya on 2006-02-20
For this

> s a side note, what IDE do you recomend for someone who wants to get into Java programming?

You can try ECLIPSE, [http://www.eclipse.org](http://www.eclipse.org)
or
NetBeans, [http://www.netbeans.org](http://www.netbeans.org)

of course there are some other IDEs, but I only had a chance to use those two.

---

