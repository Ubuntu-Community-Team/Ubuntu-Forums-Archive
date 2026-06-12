---
title: "Open office and Abiword crashes"
date: 2011-09-09
forum: General Help
---

### Post by marcia on 2011-09-09
Dear All,

I think I must have unwittingly installed something or updated something I should not have. A couple of days ago my desktop behaved differently all of a sudden. More touchy sensitive. Then when I open abiword or open office it trys to open but crashes. 

I opened open office in terminal and received this error:

$ ooffice -writer %F

 X-Error: BadDrawable (invalid Pixmap or Window parameter)
        Major opcode: 62 (X_CopyArea)
        Resource ID:  0x0
        Serial No:    475 (475)
These errors are reported asynchronously,
set environment variable SAL_SYNCHRONIZE to 1 to help debugging

I have an ati 4200 hd onboard card using the opensource ati driver, gigabyte motherboard, amd quadcore 3 ghz 945 cpu, 4 gigs memory, lucid 10.04 kubuntu, I believe.

Any suggestions or help will be greatly appreciated. Thank you.

Marcia

---

### Post by SeijiSensei on 2011-09-09
> **marcia said:**
> $ ooffice -writer %F

%F is a placeholder for the name of the file to be edited.  If you replace that with a filename, does it work?

```
$ ooffice -writer /path/to/your/doc.odt
```

What if you open it from the main KDE menu instead of the command line?

---

### Post by marcia on 2011-09-09
Thank you very much for your help. I tried opening from the KDE menu and for a second a blank document appeared and then crashed.

I then used your suggested code in a terminal and got this error message:

$ ooffice -writer /home/Desktop/htop_info.odt

~$ X-Error: BadDrawable (invalid Pixmap or Window parameter)
        Major opcode: 62 (X_CopyArea)
        Resource ID:  0x0
        Serial No:    461 (461)
These errors are reported asynchronously,
set environment variable SAL_SYNCHRONIZE to 1 to help debugging

I appreciate your assistance very much. This is above and beyond my understanding so far.

Thanks,

Marcia

---

### Post by SeijiSensei on 2011-09-10
I did a Google search for 
"openoffice X-Error: BadDrawable (invalid Pixmap or Window parameter)"
and found a lot of people reporting problems like this.  It seems to be some bad interaction among KDE, proprietary video cards, and certain apps like OO.

Why don't you try installing the proprietary ATI driver using System > Additional Drivers and see if that helps?  Are you using the openoffice.org-kde package?  Try removing that as well.

I am a bit puzzled about why both OO Writer and Abiword both crash in the same way.  That makes it sound more like a driver problem than anything else, especially since X is the system reporting the error.

BTW, trial and error has told me that Kubuntu 10.10 is the best release of KDE for Ubuntu right now.  I had problems with 10.04 (and worse problems with 11.04/11.10 beta), so I'm sticking to 10.10 for the time being.  If these problems persist, maybe you should consider installing Maverick.

I don't have your problems with OO, but I'm also using an NVIDIA card with the proprietary driver installed.

---

### Post by marcia on 2011-09-10
Thank you very much for your reply and suggestions. I just checked on abiword and to my surprise it is not crashing today. Open Office still does.

I will give some or all of your suggestions a try. Whatever works. Maybe I will try the ati proprietary driver first. 

I would like to upgrade to 10.10 if I am brave enough. My more recent upgrade was a mess and it took me 3 days to correct. My fault entirely, I know.

Thanks again for your very good research.

I will post my results.

Sincerely,

Marcia

---

### Post by marcia on 2011-09-10
Happily, I believe this is resolved. I went for the most simple suggestion first. I uninstalled the openoffice-kde. After that it now opens normally.:)

Thank you for your help.

Sincerely,

Marcia

---

