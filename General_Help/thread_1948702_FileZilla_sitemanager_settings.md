---
title: "FileZilla sitemanager settings"
date: 2012-03-28
forum: General Help
---

### Post by Nezmin2 on 2012-03-28
Hey guy's,
I know that this is an odd place for this question but I tried the FileZilla forum and they won't let me register using my gmail account. Not sure what they expect those of us who only use gmail to do.

I am running ubuntu 11.04. I have FileZilla3 installed. I want to import my FileZilla2 sites into it but nothing I have tried thus far has worked.

Thoughts???](*,)

---

### Post by superdaveozzborn on 2012-03-28
Try this method first: 
1. Start Filezilla 3. 
2. Open the **File** menu and select **Import...** 
3. Select your old *filezilla.xml* - this file is in the program directory of Filezilla 2. 
4. If Filezilla finds importable data, you'll get a dialog box  telling you that due to different formats used, you can only import  host, port, username, and password. In case of an error message try the  slightly harder way below. 
5. Answer **Yes** and your sites should be imported. 



i found this info here [http://wiki.filezilla-project.org/Fz2_to_3_convert](http://wiki.filezilla-project.org/Fz2_to_3_convert)


hope this helps ):P

---

### Post by Nezmin2 on 2012-03-28
> **superdaveozzborn said:**
> Try this method first: 
1. Start Filezilla 3. 
2. Open the **File** menu and select **Import...** 
3. Select your old *filezilla.xml* - this file is in the program directory of Filezilla 2. 
4. If Filezilla finds importable data, you'll get a dialog box  telling you that due to different formats used, you can only import  host, port, username, and password. In case of an error message try the  slightly harder way below. 
5. Answer **Yes** and your sites should be imported. 



i found this info here [http://wiki.filezilla-project.org/Fz2_to_3_convert](http://wiki.filezilla-project.org/Fz2_to_3_convert)


hope this helps ):P

I saw that site as well. The problem is that there is no "File" select in this application. I also have no preferences or options select in order to see if there is a missing tool bar or something.

---

### Post by superdaveozzborn on 2012-03-28
make shure that you can view hidden files. (ctrl H) to see .filezilla
do you still have ver2 installed? if not then you should of backed up the xml file first


should be in /home/user/.filezilla

---

### Post by Nezmin2 on 2012-03-28
> **superdaveozzborn said:**
> make shure that you can view hidden files. (ctrl H) to see .filezilla
do you still have ver2 installed? if not then you should of backed up the xml file first


should be in /home/user/.filezilla

Ok,first I did back up the file. Second, I tried copying over the filezilla.xml file in the .filezilla folder. It still does not show my sites. It is wanting something done to the sitemanager.xml file.

---

### Post by Nezmin2 on 2012-03-29
Hasn't anyone had this issue? I really like FileZilla and don't want to go to a different app but this is ridiculous.

---

### Post by Nezmin2 on 2012-03-30
I guess I am the only one having this issue. So now I guess I have to find a different FTP client. UGH!

---

### Post by Iffrit on 2012-06-06
> **Nezmin2 said:**
> I saw that site as well. The problem is that there is no "File" select in this application. I also have no preferences or options select in order to see if there is a missing tool bar or something.


When you open Filezilla, then the Ubuntu main menu (on the top) is replaced with Filezilla's menu. There you can find "File" to make the import...
Cheers,

---

