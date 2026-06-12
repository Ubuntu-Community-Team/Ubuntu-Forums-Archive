---
title: "Can't see user templates in OOo2"
date: 2006-03-21
forum: General Help
---

### Post by harnadem on 2006-03-21
A search of the forum did not reveal an answer, so I am posting a new question.

I am using Openoffice.org2-core_2.0.1_breezy and cannot see the templates that are in my user path (/home/[username]/.openoffice.org2/usr/template).  Is there a fix for this?  I can see the templates in the directory, and when I try importing them (again) from within openoffice, I get an error that the template already exists.  I just can not see them when the template function starts.  If I open the template as a document (open file) it will work fine as a template.  

I have also tried adding the templates to /usr/share/openoffice2/template/en-US (as root user) but still cannot see the templates in OOo.   Any ideas on how to fix this?

(I did notice that I have both Openoffice (1.9.125) and Openoffice2 on the system, though I did not think that this would cause any conflict.  If I need to remove OOo1.9.125 then I need some instructions on how to do that)

I have also posted this question in the OpenOffice.org forum in the hope that someone there may be able to help, but have not received a reply.

---

### Post by Zimmer on 2006-03-21
Try putting them in the hidden folder 
/home/~/.openoffice.org2/user/template (I note the location you gave shows usr, is that a typo?)
then they will appear when you click on My Templates(they do not appear in the right hand pane of the dialog, but the left hand pane when you click on My Templates). and you can then use the open button to use them ....this is the location for templates in the Ubuntu 1.9.129 version...
Regards
Zimmer

---

### Post by wjp.reg on 2006-03-21
It is my understanding that this problem was fixed in the latest oo release for ubuntu, version 2.0.2-1ubuntu3.  Have you checked for the update?

---

### Post by harnadem on 2006-03-21
[QUOTE=wjp.reg]It is my understanding that this problem was fixed in the latest oo release for ubuntu, version 2.0.2-1ubuntu3.  Have you checked for the update?[/QUOTE]

I regularly check for updates using update manager.  Do you mean that I should reinstall using apt-get?  Sorry if this sounds obvious, but I had (perhaps foolishly) assumed that the update manager would also notify me of OOo2 updates.  Thanks for your help!:)

---

### Post by harnadem on 2006-03-21
[QUOTE=Zimmer]Try putting them in the hidden folder 
/home/~/.openoffice.org2/user/template (I note the location you gave shows usr, is that a typo?)[/QUOTE]

Hi Zimmer; Yes, it was a typo.  I did place the templates into the hidden folder as you described.  They still don't show up.  I appreciate that you took the time to answer my post! :)

---

### Post by Zimmer on 2006-03-21
No worries, I guess it must be some sort of glitch with the 2* versions of OO. As I have resisted the tempatation to go outside of the official repositories for the latest version I cannot test it for you myself....sorry.
Regards
Zimmer

---

### Post by ajgreeny on 2006-03-23
Put your own templates in a sub-folder of your OOo documents (where you save documents) then when you go to the open new template dialogue, navigate to that folder in My Documents and it will show your own templates.

This is a work-around or fix I put on the forum a while ago so I'm surprised you didn't find it if you searched so here is the link.
[http://ubuntuforums.org/showthread.php?t=144329](http://ubuntuforums.org/showthread.php?t=144329)

---

### Post by harnadem on 2006-03-25
[QUOTE=ajgreeny]Put your own templates in a sub-folder of your OOo documents (where you save documents) then when you go to the open new template dialogue, navigate to that folder in My Documents and it will show your own templates.[/QUOTE]

Thanks for your reply.  This is what I had been doing (though I wasn't aware of your work around).  It is not, however, very satisfying to have a templates option, and not be able to see or use your templates.  I don't recall having this same issue with earlier versions of OOo, and wondered if the issue had been resolved.

---

### Post by secular on 2006-03-30
I found an easy workaround--if any workaround can be called "easy".

1. I cut all the templates from the folders listed in Tools->OpenOffice.org->Paths.

2. I pasted all the templates into another folder. 

3. In OpenOffice, I clicked File->Templates->Organize

4. In there, I clicked on My Templates and then clicked Commands->Import Template.

5. I then navigated to my new folder with the templates, selected all of them, and OK'd out.

It works.

---

### Post by SreckoMicic on 2006-03-31
Just type name in the Title field of your's document properties.

---

