---
title: "Cannot Install or Update Applications"
date: 2010-01-26
forum: General Help
---

### Post by sdbpastor on 2010-01-26
I am a relatively new user to Linux and Ubuntu. i have added a few applications.This morning I was attempting to add an application and thought I had followed the instructions properly but the install failed and now I cannot install any application through the package manager nor check for updates through update manager.

I get the followng error message:

E: Type 'Remmina' is not known on line 64 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

How can I correct ths?

Thanks,
Michael

---

### Post by snowpine on 2010-01-26
Hi Michael, you messed up your software sources. Try:

```
gksu gedit /etc/apt/sources.list
```

Scroll down to line 64 and comment out the line by typing a # symbol at the start of the line. (This will make the system skip that line next time.) You can copy & paste the contents of the file here if you want us to take a look at it for you. Don't forget to save your changes.

Once you've fixed your software sources as I described above, let's talk about what you are trying to install and how. Generally speaking, you can find thousands of applications in the official Ubuntu "repositories" using the Software Center or Synaptic Package Manager. You should not edit your system files (such as /etc/apt/sources.list) unless you know exactly what you're doing and why.

---

### Post by hhlp on 2010-01-26
execute this command in a terninal :

[PHP]sudo cat /etc/apt/sources.list > source.txt[/PHP]

and upload that file to the post to see what happened

---

### Post by sdbpastor on 2010-01-26
Thanks! That did the trick. i was attempting to install the 'Remmina' Remote Desktop application but have now decided against it since getting VNC and Gnome-RDP connecting from Ubuntu to Vsta.

Thanks again.
Michael

---

