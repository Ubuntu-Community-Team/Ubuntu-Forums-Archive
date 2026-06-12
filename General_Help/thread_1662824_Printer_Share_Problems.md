---
title: "Printer Share Problems"
date: 2011-01-08
forum: General Help
---

### Post by kmccmk9 on 2011-01-08
Hello, I'm trying to print files to a printer that is connected to my Ubuntu machine. Basically the printer server (and client) is the Ubuntu machine. The other client machine is a Windows 7 laptop. I have followed many tutorials and guides on how to enable printer sharing. For some reason I can't get the printer to be listed as an available printer. Any help would greatly be appreciated.

---

### Post by RedSingularity on 2011-01-08
You cannot even get it to show up on the local machine?  What printer is it?

---

### Post by davidvandoren on 2011-01-08
If you have a stable IP for the Internet you could print over the Internet instead of the local network. 

On a Gnome desktop; go to **System / Administration / Printing**
Then go to [B]Server / Settings

[/B]Select 
**show printers shared by other systems**
         
** publish shared printers connected to this system**
          
 **allow printing from the internet**

click [B]OK 


[/B]Right click the printer you want to share 
            It should say **enabled** 
                                    [B] shared


[COLOR=SeaGreen]Install firewall configuration and open port 631

[/COLOR][/B][COLOR=SeaGreen][COLOR=Black]On windows 
go to **ad printer**
select [/COLOR][/COLOR] [B]Network printer
[/B]click **Next**
select **Connect to a printer on the internet **
**enter the printer URL**
**[http://[COLOR=Red]your](http://[COLOR=Red]your) internet ip[/COLOR]:631/printers/[COLOR=Red]printer's name[/COLOR]**[COLOR=Red]

[COLOR=Black]On ubuntu put this url into your browser to see your printer's name 
[/COLOR][/COLOR]**localhost:631/printers/** incl. http://

---

### Post by kmccmk9 on 2011-01-10
> **davidvandoren said:**
> If you have a stable IP for the Internet you could print over the Internet instead of the local network. 

On a Gnome desktop; go to **System / Administration / Printing**
Then go to [B]Server / Settings

[/B]Select 
**show printers shared by other systems**
         
** publish shared printers connected to this system**
          
 **allow printing from the internet**

click [B]OK 


[/B]Right click the printer you want to share 
            It should say **enabled** 
                                    [B] shared


[COLOR=SeaGreen]Install firewall configuration and open port 631

[/COLOR][/B][COLOR=SeaGreen][COLOR=Black]On windows 
go to **ad printer**
select [/COLOR][/COLOR] [B]Network printer
[/B]click **Next**
select **Connect to a printer on the internet **
**enter the printer URL**
**[http://[COLOR=Red]your[/COLOR]]("http://%3Cfont%20color=%22Red%22%3Eyour%3C/font%3E")[COLOR=Red] internet ip[/COLOR]:631/printers/[COLOR=Red]printer's name[/COLOR]**[COLOR=Red]

[COLOR=Black]On ubuntu put this url into your browser to see your printer's name 
[/COLOR][/COLOR]**localhost:631/printers/** incl. http://

Ok I did all of this and Windows still can't find the printer. The link I used was this

[http://myipadresshere:631/printers/PSC-2170-Series]("http://192.168.1.16:631/printers/PSC-Photosmart-Series")

It claims it can't find the printer on the network and is asking for additional information. I chose generic network card. Then I need to find the printer in the list. for a driver. I choose my printer HP PSC 2170 Series. It proceeds to install printer with the correct driver. It does it tells me its ready to print. But I can't get anything to print. I even check the job status after sending a job and it never gets there.

---

### Post by drdos2006 on 2011-01-10
Windows 7 desktop needs a Windows server with attached printer.
Windows has removed the Internet Printing Protocol from Windows 7.
There is a patch from Microsoft but I could never get the patch to work.
You need to google on "windows 7 printing".

regards

---

### Post by kmccmk9 on 2011-01-10
> **drdos2006 said:**
> Windows 7 desktop needs a Windows server with attached printer.
Windows has removed the Internet Printing Protocol from Windows 7.
There is a patch from Microsoft but I could never get the patch to work.
You need to google on "windows 7 printing".

regards

ugh stupid Windows! Ok is it possible to print to the printer if I connect my Windows laptop via usb cable to the Ubuntu Desktop computer?

---

