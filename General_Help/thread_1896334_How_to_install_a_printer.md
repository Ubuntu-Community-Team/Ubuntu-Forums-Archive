---
title: "How to install a printer?"
date: 2011-12-16
forum: General Help
---

### Post by pieroxy on 2011-12-16
I feel stupid tonight. I've installed my printer before, but this time I just can't figure out how to do it...

I have a networked printer and I've installed it on my previous Ubuntu installs by just going to the "printer" section of the "System" menu and then it was automatically detected. A breeze.

Now, on the greatest and latest Ubuntu, I go to "System Setting", I see a "printers" icon and when I click on it, an empty list along with a disabled "add printer" button shows up...

How the f**ck does that work?

---

### Post by Sleepy-zz-John on 2011-12-30
I have the same problem,  except that I'm trying to install a hardware printer on 11:10 Ocelot.     When I go to System Settings -> Printers,  everything is greyed out,  including the "Add New Printer" button.   Where do we start?

---

### Post by Mark Phelps on 2011-12-30
Try using CUPS to do this.  Open a browser, enter "localhost:631".

When CUPS starts, use the option to Add a printer.  You should see your printer already detected under the list of network printers.

---

### Post by Sleepy-zz-John on 2011-12-31
Thanks Mark,   I've tried CUPS but since my yesterday's post seem to have moved a step backwards.    Yesterday I installed a Xerox Docuprint 4508 Foomatic/ljet4 [en]  which I wrongly guessed might be the best driver for my printer which is actually a Fuji Xerox Docuprint 203A.   Now I want to delete that and try some different drivers instead because although it's sitting comfortably in my system and responding to print commands,  all pages are coming out blank white.    How can I delete an installed printer,  either from within CUPS,  or directly in Ocelot's System Settings -> Hardware -> Printers or by Terminal command line?

---

### Post by Pilot6 on 2011-12-31
Why don't you press this button 'Add printer' and add your printer? What is the problem?
I also have network printers. After you press the button you will see a dialog where you can browse network printers and choose drivers if they are not detected automatically.

---

### Post by rjf1 on 2011-12-31
To delete your printer from CUPS:
Open CUPS in your browser (localhost:631)
Select Printers (top right)
Click the printer you want to delete > Administration > Delete Printer

---

### Post by ElanCompaq on 2011-12-31
if the drivers are for windows then i think that the simba ( cant remeber what it was called exactly ) will give many choices.

---

### Post by Sleepy-zz-John on 2011-12-31
Thanks Pilot6 and thanks rjf1.  That's now worked and I've been able to add a new printer under my existing heading,  see that it prints OK,  and delete the original printer with the dud driver I'd previously installed,  so now  :biggrin:

T'wasn't entirely intuitive,  I have to say tho'.   First I thought the name and driver I'd first entered were linked in the same data and I'd have to delete the whole lot at one go.  Second,  on trying to delete, I'd got as far as rjf1's 3rd line,  but missed the options under Administration.  How to delete a printer is well hidden in the documentation as my searches for "delete printer" yielded no results.  

Anyway,  got there in the end,  thanks.  :)

---

### Post by jwaipouri on 2012-04-11
Hey guys
I'm trying to install a Fuji Xerox DocuCentre IV-C2270.
I downloaded, and converted an RPM linux driver. When I go to add it as the driver for the printer, I get the error message "server-error-internal-error"
Anyone got any help for me on this?

Acer Aspire. 1.60GHz 
10.04LTS
Networked printer

---

### Post by blackangelpr on 2012-04-11
as other had reply i can only write that in my case with the latest ubuntu version the HP printers had been working great only because i found hp ubuntu drivers i highly recommend to go to the printer manufacture and look for those.. in my case they done a terrific job in the drivers and its a land printer..):P

---

