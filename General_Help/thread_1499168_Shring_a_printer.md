---
title: "Shring a printer"
date: 2010-06-01
forum: General Help
---

### Post by David Deu on 2010-06-01
Hi,
I got my printer on my other PC which is (still) running Windows, it's shared in the network and I'm able to print with other PCs.
How do I share that printer with Ubuntu too?

Thanks,
David

---

### Post by pricetech on 2010-06-01
System - Administration - Printing.  Click the Add button.  You should be able to set it up by scanning for a network printer.

---

### Post by David Deu on 2010-06-01
I'm aware of this guide: [https://help.ubuntu.com/community/WindowsXPPrinter](https://help.ubuntu.com/community/WindowsXPPrinter)
But the problem is, that from some reason no one of the options in the "printing" window are available (except  "help, about, connect, exit and may be I forgot one).

---

### Post by Morbius1 on 2010-06-01
Is CUPS running?
```
sudo service cups status
```If not the restart it:
```
sudo service cups restart
```

---

### Post by David Deu on 2010-06-01
I had actually had to install the 'cups' and I did.
now, I found the printer on the network but then at the driver part, my model doesn't appear there, so I've checked on Brother's website, and I saw there are a few types of files to download/install, how do I know which of them is for me?

Thanks,
David

---

### Post by anilw3 on 2010-07-12
Hello, will I have to do this everytime I want to use my printer?
thanks

---

### Post by anilw3 on 2010-07-12
> **Morbius1 said:**
> Is CUPS running?
```
sudo service cups status
```If not the restart it:
```
sudo service cups restart
```


Will I have to do that everytime I want to use my printer?
thanks

---

### Post by Morbius1 on 2010-07-12
> **anilw3 said:**
> Will I have to do that everytime I want to use my printer?
thanks
If you're using Ubuntu prior to 10.04 I would say no. But the current version has problems starting certain services or at least starting them in the right sequence. If you find yourself having to start it at every boot then I would suggest this workaround: [http://ubuntuforums.org/showpost.php?p=9405854&postcount=4](http://ubuntuforums.org/showpost.php?p=9405854&postcount=4)

---

