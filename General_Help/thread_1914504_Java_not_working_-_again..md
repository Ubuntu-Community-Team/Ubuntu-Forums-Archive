---
title: "Java not working - again."
date: 2012-01-24
forum: General Help
---

### Post by mystmaiden on 2012-01-24
I'm not sure what causes this but from time to time Java seems to just quit working. I'm running Lucid lts and using sun java. An attempt to configure returns 'nothing to configure'. Java is enabled in Firefox. This is kind of important at this point because I need to do a web seminar that's only available in java.

thanks,
mystmaiden

---

### Post by QIII on 2012-01-24
How did you install java?

Did you recently upgrade to FireFox 9?

What are the results of

```
java -version
```

---

### Post by mystmaiden on 2012-01-24
Thank you, QIII for the reply. I think I have complicated the whole issue by attempting to follow the instructions found at  [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java) . I deleted the current Java folder (though it was not found in opt) so java --version brings no results.

I am running firefox 3.6.24 and I think the Java version was too old to work with it (sun java site said I needed update 10 or better). Looks like I am starting from scratch...

mystmaiden

---

### Post by QIII on 2012-01-24
That link is the best one I have found in terms of simplicity and effectiveness.  But you should copy and paste if you can.  Typing can lead to mistakes.

---

### Post by mystmaiden on 2012-01-24
I can not actually remember how I originally installed java. I did run into a couple of problems with the instructions on the website I listed though. The first one - 
```
$ cd /opt
bash: cd: /opt: No such file or directory


```so if I run the next command - sudo mkdr java as is, where will it make the directory? Is opt the same as /etc?

---

### Post by QIII on 2012-01-24
Are you following the directions to the letter?  Creating the /opt folder is a part of the process.  

/opt is not the same as /etc

Edit:  come to think of it, /opt may be created when you install Ubuntu now.  If it's not there, did you delete it?

---

### Post by mystmaiden on 2012-01-24
I've not deleted the /opt file at any point. I'm using Lucid, was the opt file created at install with Lucid?  Where is it usually?

And I can't honestly say I'm following the directions to the letter though  because for 

QUOTE]Go to the folder opt:
Click on the grey Ubuntu logo (Dash home). Query: terminal. Click on Terminal.[/QUOTE]

I wasn't really sure what all that meant, I just navigate to applications/accessories/terminal when I need the terminal.

Beyond that, yes I copied the exact command into the terminal. Although, the way I read this it seemed like I would be creating a folder within /opt rather than creating opt?

---

### Post by QIII on 2012-01-24
```
sudo mkdir /opt
```

Should work, I believe.  That probably used to be part of the instructions.

---

### Post by mystmaiden on 2012-01-24
Thank you so very much QIII - Java is now installed and working perfectly. You rock.

mystmaiden

---

### Post by QIII on 2012-01-24
I can't take any credit. That goes to the folks who maintain that tutorial.

---

### Post by Pjotr123 on 2012-01-24
/opt is a system folder, and is being created automatically during installation of Ubuntu (and of every other Linux distribution that I know). 

Present by default, in any clean installation. General usage: the spot to install third-party applications.

If /opt is not there, then you must have previously deleted it yourself... :)

---

