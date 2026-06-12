---
title: "Intalling and using the Striata Reader on Ubuntu"
date: 2010-06-26
forum: General Help
---

### Post by datraveller on 2010-06-26
**Installing the Striata Reader on Ubuntu**
 Note: Ubuntu is case sensitive so please always type using the correct case e.g. *Desktop* not *desktop*
 
[LIST]
[*]Download the Striata Reader (Linux     – libc6 - compatible with Ubuntu) at the following link:     [http://www.striata.com/resources/striata-reader/striata-reader-linux-libc6/download.html](http://www.striata.com/resources/striata-reader/striata-reader-linux-libc6/download.html)
[*]Extract the attached     *striata-reader.tar.gz* file to a *Striata *folderin Ubuntu's default *Desktop*     folder. To extract the contents open downloaded file, click     *Extract, *navigating to the *Desktop* folder, creating     the new folder naming it *Striata*,  opening the new *Striata     *folder and then click *Extract*.
[*]Now open the Ubuntu Terminal by     clicking:* Applications->Accessories->Terminal*
[*]In the *Terminal* window     change the directory to the *Striata* folder where you     extracted the downloaded files to by typing: *cd Desktop/Striata *
[*]Check to see if the *install*     and s*triata-reader* files are in this directory by typing: *dir*
[*]If no files     are listed check that the files were extracted to the correct     directory and that you are in the correct directory by re-performing     the above steps.
[*]While sill in the *Desktop/Striata*     directory in the *Terminal*     window type the following command: *sudo sh install*
[*]You will then be prompted to enter     your Ubuntu password
[*]Once the password has been     accepted you will be asked which Internet browser you are using and     if you are using Ubuntu it will most likely be ForeFox option: *1*.
[*]Once the Striata Reader is     installed correctly, you will need to follow the below instructions     every time you open a Striata Reader file (*.emc).
[/LIST]
 

 

 **Opening a Striata file (*.emc) in Ubuntu once the Striata Reader has been installed**
 Note: Ubuntu is case sensitive so please always type using the correct case e.g. *Documents* not d*ocuments*
 
[LIST]
[*]Save the Striata file you want to     open to a new folder in Ubuntu's default *Documents* folder.     Keep the name of the new folder and the file short and do not use     any spaces e.g. folder name: *Statements* document name:     *201005BankA.emc*
[*]Open the Ubuntu Terminal by     clicking:* Applications->Accessories->Terminal*
[*]In     the *Terminal* window     change the directory to the where the Striata file that you are     wanting to open is located. E.g. type: cd *Documents/Statements*
[*]Now     open the file you are wanting to open using the installed*     striata-reader *program. Please     note that when typing the Striata file you will need to include the     *.emc* extension e.g.     type: *striata-reader 201005BankA.emc*
[*]The     selected document should now open in your selected browser, e.g.     FireFox, once you have completed the required password prompt.
[*]If     you are struggling to navigate to the folder created check that the     file is in the correct folder using the Ubuntu file browser then     close the *Terminal*     window and start again.
[/LIST]

---

### Post by pfene on 2010-06-27
Thanks for the post Bra , now i can read my statements, how-ever is the no way to just double click to open the e file.

---

### Post by datraveller on 2010-06-27
> **unutbu said:**
> In Nautilus, the Ubuntu default file browser,  right-click on the .emc file. Select Properties>Open With. A list of  apps will pop up. If Striata Reader is not in that list, click  "Add">"Use a custom command" and type in striata-reader.

The above suggestion seems to have worked for others but when I try this nothing happens. Try it and let me know if it works on your side.

---

