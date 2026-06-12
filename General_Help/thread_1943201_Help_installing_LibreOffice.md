---
title: "Help installing LibreOffice"
date: 2012-03-19
forum: General Help
---

### Post by mike64485 on 2012-03-19
Not much experience installing from Terminal: 

I am trying to install LibreOffice on Ubuntu 10.04. I get as far as "right click on the file and choose 'Open in Terminal' " --  but that choice does not appear on the drop down list.

If I choose "Open with Other Application", Terminal is also not an available choice.

If I simply open Terminal I can't find the directory with the LibreOffice files.

Will someone please help me.

Thanks
Mike

---

### Post by mike555 on 2012-03-19
Use the synaptic package manager.

---

### Post by simptechmike on 2012-03-19
> **mike555 said:**
> Use the synaptic package manager.

I too would recommend using the synaptic package manager. If you wish to install through the terminal though, with the terminal window open enter the following:

sudo apt-get install libreoffice

enter your password

---

### Post by philinux on 2012-03-19
> **mike64485 said:**
> Not much experience installing from Terminal: 

I am trying to install LibreOffice on Ubuntu 10.04. I get as far as "right click on the file and choose 'Open in Terminal' " --  but that choice does not appear on the drop down list.

If I choose "Open with Other Application", Terminal is also not an available choice.

If I simply open Terminal I can't find the directory with the LibreOffice files.

Will someone please help me.

Thanks
Mike

I dont know how you are doing this but this is a good way. Since 10.04 needs a ppa for libreoffice as it only started being included in Ubuntu 11.04. The instructions are very clear.

[https://wiki.ubuntu.com/LibreOffice](https://wiki.ubuntu.com/LibreOffice)

---

### Post by ajgreeny on 2012-03-19
I definitely recommend using the ppa and synaptic as it overcomes all sorts of problems that you may otherwise encounter.

If you really want to use the archive you have downloaded, after you have unpacked it, you will probably find a folder somewhere in the hierarchy called debs which contains all the separate .deb files.  In terminal navigate to that folder with ```
cd path/to/folder/debs
``` then run ```
sudo dpkg -i *.deb
``` You can not install the packages very easily one by one as they are interdependent.

I think this way, it it works as OOo used to, will install LO in /opt and leave OOo as it was, perhaps a bit confusing, hence my recommendation to use the ppa and synaptic

---

