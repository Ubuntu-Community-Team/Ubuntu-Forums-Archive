---
title: "dual boot options"
date: 2010-05-18
forum: General Help
---

### Post by FM101 on 2010-05-18
Hello,
I have a dual boot environment.  Windows 7 and ubuntu 10.04.
when booting up I get 2 choice screens.
1) windows and ubuntu 
2) ubuntu, ubuntu recovery, windows 7

Is there a way to do a straight boot into regular ubuntu?  Some app (setting) in ubuntu?

With the ability to turn back on the boot manager (from inside ubuntu) if ever needed.

thanks

---

### Post by ubunterooster on 2010-05-18
you want the "startupmanager" app

---

### Post by FM101 on 2010-05-18
thanks ubunterooster,
will that configure both boots?
is that an app that needs to be installed?  not pre installed on 10.04?

---

### Post by ubunterooster on 2010-05-18
[COLOR=Blue]will that configure both boots?[/COLOR] Yes
[COLOR=Blue]is that an app that needs to be installed?[/COLOR] Yes; you can get it via synaptic (or apt-get)

---

### Post by pizza-is-good on 2010-05-18
you can get it by typing:
```
sudo apt-get install startupmanager
```
on your terminal.

You can there set the entry that you want to boot default into and the time that you want it to wait.

---

### Post by FM101 on 2010-05-19
Hi,
I installed startupmanager.  Not many options.  But I set the time to 0.  Is that correct?
I still get the first boot choice.  I looked in f12 and f2.  did not see any good options.  is there a way to get rid of the first boot choice? 

After I make that choice, I get a blank screen for 15 seconds before the ubuntu start up screen starts up.  should that be normal.

thanks

---

### Post by ubunterooster on 2010-05-19
Not normal; as per changing default, do these screenshots help?

---

### Post by wilee-nilee on 2010-05-19
Setting the count down to 0 is not a good idea, there are reasons why, in that if you have a failure to boot in normally, It is very difficult if not impossible to access the command and edits within the grub list. So set it to at least 1 second 3 is better. Grub is different then a windows boot where you can hit f8 to get to controls and a command line soon as it starts up. If you set grub countdown to 0 you are setting yourself up for a major problem possibility.

---

### Post by ubunterooster on 2010-05-19
Hmm good point; I have mine set to "1" personally. Forgot to mention that; thanks for reminding me, wilee.

---

### Post by wilee-nilee on 2010-05-19
> **ubunterooster said:**
> Hmm good point; I have mine set to "1" personally. Forgot to mention that; thanks for reminding me, wilee.

Like once a year if I'm lucky I'm sort of correct, now where is the champagne. ;)

---

### Post by FM101 on 2010-05-19
I set my startupmanager to 1 and I still get the a blank screen for 15 seconds before the ubuntu start up screen starts up.
I have attached a screenshot.  I do have less options.

Also, do you know how to remove the windows boot loader?

thanks


[[IMG]http://img22.imageshack.us/img22/9441/desk1001.jpg[/IMG]](http://img22.imageshack.us/i/desk1001.jpg/)</noscript>

---

### Post by ubunterooster on 2010-05-19
Do you want to remove the windows entry? How will you then get into windows?

try ```
sudo update-grub
```

---

