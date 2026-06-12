---
title: "failed to mount files system ..windows"
date: 2009-09-02
forum: General Help
---

### Post by gaurav sontakke on 2009-09-02
Hi All
     I have installed ubuntu 9.04 on  client and created one active directory login for this ubuntu system.Server is in windows Windows Server 2003.
              
                     I have successfully created the domain account but whenever I try to access windows files from my server it gives me error like

                                           **[SIZE=5]Unable to mount Location[/SIZE]**
                         [SIZE=5]**[COLOR=Black]Failed to retrieve share list from server[/COLOR]**[/SIZE]

what should be the problem. I have created domain not the workgroup.



Please help me out..


                    Thanking You






Regards 

Gaurav Sontakke

---

### Post by P4man on 2009-09-02
A few things you can try. On the ubuntu client, go to places > connect to server. Select windows share, fill out all information and make a bookmark.

If that fails, try following this:

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by gaurav sontakke on 2009-09-03
thank you 
       I have tried but still my problem is same Is there any change which I have to do at server side.??means windows machine side???


         Also my ubuntu machine connected to network are unable to access each others files..
It does not show my linux machines at my network places.

 And if  I try to access issuing command 
               sftp://ip


It gives me error such as 
[SIZE=5]
                 ACCESS WAS DENIED[/SIZE]


What should be the problem???

         Thanking You


Regards
Guarav Sontakke

---

### Post by P4man on 2009-09-03
did you follow all steps in that link? Especially changing the ubuntu "workgroup" in to your windows domain name and changing the firewall settings?

---

### Post by gaurav sontakke on 2009-09-03
yes I have followed each and every step in the file..
But still the problem is same..
         But what should be the problem with my ubuntus machine..
They are also not accessing each others file..

            And also ubuntu machines are not showing in network window...




Thanking you 









regards
Gaurav Sontakke

---

