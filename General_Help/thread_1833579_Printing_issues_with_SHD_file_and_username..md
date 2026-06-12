---
title: "Printing issues with SHD file and username."
date: 2011-08-26
forum: General Help
---

### Post by ozanamn on 2011-08-26
Hey Guys,

Can anybody give any ideas on the exchange of mails below.

In Short we use a system to retrieve documents from the printer via the users network user name and all this works fine through samba.

Put this perticualar linux box is puting the user ID in a SHD file but for safecom(the printing sytem) to read the user ID it needs to be in the spool file.

Cheers,
Scott 

----------------------------------------------------------

Hi Jason,

I am not full sure how it works in linux, so I cannot name the specific files, but there will be some sort of a model script that the print file is piped through, which will send the print job onto the printer.
 
The trick is insert the correct line in another file, and send both the line and the print file into the model script at the same time. This can be done either at the beginning of the model script or at the point where the model script is called.
 
When the model script is called, I would expect the system to be doing something like:
 
Cat $PRINTFILE | model_script
 
We want to change that to be:
 
Cat $HEADERFILE $PRINTFILE | model_script
 
But &#8211; It may be that we need to create the $HEADERFILE beforehand, to hold the correct username etc.
 
It would be really quite useful if we could create the exact instructions for this. I&#8217;d be happy to help with that, if we can get some time on the customers system to play with this, but ideally not having somebody looking over our shoulders? Do you think they are friendly enough for us to get that?
 
Pete
Peter Ronayne


----------------------------------------------------------------
  
From: Jason Quinn 
Sent: 24 August 2011 15:26
To: Ronayne, Peter
Subject: Linux printing with SafeCom
 
Hi Pete
 
Hope your well. Do you have any idea how to create a PJl cmd and insert it into a linux print job.  Safecom have given us this information but the customers linux team are unsure of where to start.
The user name is contained in the SHD file but SafeCom requires it in the spool file.
 
Any help would be appreciated
 
Regards
Jason
 
Hi Bob,
 
Here is the rough example (Pull queue and job data string.docx), and very limited tech note for Unix print (Safecom_tech_note_unix_printing_20114-01.pdf) and more specific Novell iPrint configuration (safecom_tech_note_novell_iprint_and_safecom_20125-01.pdf) and more comprehensive SAP configuration guide (safecom_tech_note_configure_SAP_output_device_for_safecom_pull.pdf).
 
So here are the good, the bad and the really ugly guides for all sorts of non-windows prints.
 
Thanks,
Filip

---

### Post by ozanamn on 2011-08-29
Bump,

Anybody any suggestions.

---

