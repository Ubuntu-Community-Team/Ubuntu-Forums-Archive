---
title: "Brother MFC-8840D printing woes."
date: 2010-03-25
forum: General Help
---

### Post by robsoles on 2010-03-25
Hi All,

When my boss tries to print a receipt from his online banking he first gets a page from the Brother MFC-8840D containing only the following text;

---
ERROR NAME;
    configuration error
COMMAND;
    setpagedevice
OPERAND STACK;
    --dicttype--
---

(** Please see [http://ubuntuforums.org/showthread.php?t=296109](http://ubuntuforums.org/showthread.php?t=296109) and understand that I would have preferred to continue the only thread Google indicates on [www.ubuntuforums.org]("http://www.ubuntuforums.org") regarding a similar error and behavior, also on a brother printer)

But if my boss repeats his actions at his PC the blasted thing prints out correctly. If he sends it to the Dell printer in the office it simply prints but being a color printer and some color on the page it is not economical for him to just send it there all the time.

He is on Ubuntu 9.10, 32 bit using Firefox as the app trying to print. He has a VM in VirtualBox of WinXP and from there (as with all windows machines accessing this printer) it just prints fine, the other fellow in the office using Ubuntu has exactly the same problem - send it twice if this is not his VM because the first attempt will be one page of 'error' as above.

I've tried with alternative programs and all the ones I have tried exhibit this same behavior so I am not inclined to blame Firefox - there is an archived thread where someone mentioned this exact behavior, on a Brother printer, back in December 2007 - doesn't fill me with confidence that this will be resolved too quickly but...

Please help.

TIA.

---

### Post by jimv on 2010-03-25
Do you have the official Brother driver?

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-8840D](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-8840D)

---

### Post by robsoles on 2010-03-25
I downloaded it but if I can avoid installing it I certainly will and so far I am not convinced it must be installed. The printer has delivered many pages looking exactly like they do from the Dell but in B&W using the driver I can find in the 'add printer' dialog in Ubuntu.

I think the driver Ubuntu comes with is perfectly usable if it is the only one/type sending jobs to the printer, I didn't notice before but if no job comes from a WinXP box between jobs from the Ubuntu box there is no error page (so far while paying attention to this).

Printer manufacturers seemed to put a lot of effort into taking over my PC if I installed their software in the early 90s and it taught me to try really hard with my O/S vendor's copy of printer drivers before using anything from a printer manufacturer.

I guess I'll have to install their driver in at least one of the Ubuntu systems with access to that printer, check it for undue use of system resources and then try printing with it after a Windows machine has printed on that Brother.

Actually a bit embarrassed I started this thread without trying their driver, I really should set up a trashable Ubuntu VM on work's network

---

### Post by jimv on 2010-03-25
Brother's pretty good about not putting crapware on your machine.  I'm pretty sure that these are just the drivers since they're only ~30 kilobytes.

---

### Post by robsoles on 2010-03-25
Thanks for the reassurance jimv but I seem to have installed 100K+ to make it work a bit more seamlessly.

At least I won't be called to the office over it  again (for now) - I should submit bug reports over a couple of details I  will mention below but I doubt I have the time to dig up all the logs  etc they ask for if you make such a report.

The ppd file Brother supply is every bit as good as the one that Ubuntu  comes with - still a waste of at least one page to try to print after a  Windows system has sent a print job. I think this is a simple *BUG* that  is actually Brother's fault as opposed to anyone else (ask, I will  happily explain).

The cupswrapperMFC8840D setup indicated a requirement of the LPR  'filter' and failed - GUI package installer made it look like it didn't  actually install by offering to 'install' it instead of 'reinstall' but BASHing "sudo dpkg -r cupswrapperMFC8840D" made it  look like it had, however broken - this freed up something like 90K  of HDD space...

...
Installed BSD-LPR: had to do a bit of research on what exactly "To  Remove: ubuntu-desktop" meant, ok "MOSTLY HARMLESS" - perhaps a little  more work to upgrade later.

mfc8840dlpr.deb installed Ok, cupswrapperMFC8840D installed Ok - the  completion of these steps added a defunct "MFC8840D" printer to the list  of printers in the Printer manager trying to communicate on a USB port. The Printer Manager appears to have a serious *BUG* - has anyone else  tried to use the GUI printer manager to change settings on any of their  printers in 9.10? 

I changed the settings for this new printer to use  smb:\\(private-info)\brother8840d and found that the Apply button didn't  become enabled and there was no setting on any tab of that dialog that I could change to make the Apply button activate - only 'cancel' or closing the window were available to me at all times and as they shouldn't, neither of those applied my settings.

I had to delete the printer and install using "New" to switch to the  Brother supplied PPD file, I deleted that printer and the defunct  printer the Brother installer gave me and selected "New" again, into the  list of printers and selected Brother again, in the list of Makes was a new entry (third where only two before) "MFC8840D for CUPS" and I  chose it - presto, one Ubuntu host that can follow a Windows machine in  the print queue on the Brother, yay!

I was able to fairly well completely confirm that both PPD files (from  Ubuntu installer and from Brother themselves) **only** suffered an error page if  there was a print job from a WinXP machine between jobs from the Ubuntu  host. The other Ubuntu host I haven't "fixed" has same problem following  the 'fixed' Ubuntu host now as if it is following one of the Windows  machines.

I will remain subscribed to this thread, till it's obviously dead, on the offchance that anyone wants to share anything related or perhaps even interrogate me a bit about statements I've made.

Rob.

---

### Post by daves1646 on 2010-04-11
The print bug, agreed likely from Brother, has been in Ubuntu since at least Hardy, and since the MFC-8440D is not a current product, I'd be surprised if we get any relief from the problem with an updated driver from Brother that is then pulled into Ubuntu.  I've had no success trying other close in vintage printer drivers - don't appear to share enough driver code to make using another printer's driver a workaround that could pulled forward through versions and updates.

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/306401](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/306401)

---

### Post by robsoles on 2010-04-13
Perhaps my latest embarrassment can help others.

I was pursuing the problem of getting the brother mfc8840d drivers onto the 64 bit install of Ubuntu 9.10, about to compile the source code I eventually found on the brother website when it occurred to me to try something possibly a bit silly;

I opened 'Synaptic Package Manager' from 'System'->'Administration' and typed in 'brother' - lo and behold, packages with many printer models all ready to be installed in a jiffy!


Before going to any further trouble just try opening the synaptic package manager and type in something from the name of your device '8840D' would have been the quickest search I could make in my case, making it 'mfc8840d' wasn't found because of the way it is listed in the description of the package.

I'd love it if they'd fix the ppd file on it's own for this printer but I think I've discovered why they simply won't bother - fixed already in packages available via synaptic!

I remain subscribed...

---

