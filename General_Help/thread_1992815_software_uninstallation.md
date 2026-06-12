---
title: "software uninstallation"
date: 2012-05-31
forum: General Help
---

### Post by nashtrik on 2012-05-31
I downloaded Foxit reader,a PDF file reader from its website and installed on 11.10 through the software center. While installation,the status bar filled completely but did not end with a green check mark indicating as 'Installed'. Now when I open the application through Applications--> Foxit reader,nothing happens.If i want to reinstall it again,same thing happens.The installation bar fills to the maximum,but does not show as 'Installed'.I am unable to remove the software through the terminal with ' sudo apt-get remove FoxitReader ', the message is, 'unable to locate the program'....How to remove this program...?

---

### Post by Lars Noodén on 2012-06-01
I'm guessing you got the .deb package from here:

[http://www.foxitsoftware.com/pdf/desklinux/download.php](http://www.foxitsoftware.com/pdf/desklinux/download.php)

and installed that.  I'm not sure how to force the Software Center to obey and list the independent programs that are installed as it should.  [dpkg](http://manpages.ubuntu.com/manpages/precise/en/man1/dpkg.1.html) finds it just fine, if it really is installed.  

```

dpkg --get-selections foxit*

```

To remove it, you want lowercase:

```

sudo apt-get remove foxitreader

```

Problems like these are why it is always a better idea to stick with what's in the repository.  Have you looked at Evince and Okular yet?

---

### Post by drpjkurian on 2012-06-01
You can check for the package of the programme in synaptic package manager and remove it

---

### Post by nashtrik on 2012-06-01
@Lars:--Thanks a lot..I will definitely give it a shot tonight.No,I haven't looked at Evince and Okular. Could you please shed some light on them...?

---

### Post by Lars Noodén on 2012-06-02
Evince and Okular read PDF files for you.  They are both in the repositories so they are easy to install with Synaptic or the Software Center.  They are also easy to uninstall, so you can try either or both at no risk.

---

