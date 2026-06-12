---
title: "CNC Lathe"
date: 2009-12-21
forum: General Help
---

### Post by Rexhunt on 2009-12-21
At school we have an old cnc lathe that hasn't been working for the past 15 years and I am the first person to get it to work. However the computer interface is an old dos based one that I feel a number of people may have trouble getting used to as there is only a keyboard.
The computer that is currently running the software is an old 486? with a 100 mhz processor. there are some pentium 3's that are being thrown out so I can get one of those.
 
The lathe is an emco compact 5 PC not a compact 5 cnc.
 
thanks in advance.

---

### Post by deathbyswiftwind on 2009-12-21
so what exactly is the question? if it will work?

---

### Post by Iowan on 2009-12-21
Sounds like an interesting challenge!

---

### Post by hansdown on 2009-12-21
Hey, that's pretty cool.

[http://www.youtube.com/watch?v=Lk1xhYyi-o4](http://www.youtube.com/watch?v=Lk1xhYyi-o4)

[http://www.youtube.com/watch?v=D4PrCejPbZ8](http://www.youtube.com/watch?v=D4PrCejPbZ8)

[http://www.lathes.co.uk/emco/page11.html](http://www.lathes.co.uk/emco/page11.html)

---

### Post by Rexhunt on 2009-12-21
Sorry I may not have explained myself properly.
 
The lathe works with the dos software.
 
So far I am the only person who has actually used the lathe to cut something.
 
I belive this is because the interface is an old one and I may very well be the only person in the school who is comfortable with an old dos (mouseless) interface.
 
I am hoping that there will be some software that will allow me to setup a more intuitive interface even if I have to add some extra components to the software.
 
I also wish to not change the lathe in any way shape or form as if it is not modified then it will always work with the origanal software
 
Hope this clears things up.

---

### Post by alexfish on 2009-12-21
Home of the **E**nhanced **M**achine **C**ontroller project, (or simply **EMC**) 

Worth reading

EMC2 is Free software released under the terms of the[ GNU GPL (General Public License)]("http://www.gnu.org/copyleft/gpl.html").

[http://www.linuxcnc.org/](http://www.linuxcnc.org/)

---

### Post by hansdown on 2009-12-21
Linuxcnc.org looks promising.

[http://www.linuxcnc.org/](http://www.linuxcnc.org/)

---

### Post by alexfish on 2009-12-21
> **hansdown said:**
> Linuxcnc.org looks promising.

[http://www.linuxcnc.org/](http://www.linuxcnc.org/)



EMC2 is precompiled with Ubuntu LTS (long term support) versions for ease of installation and longevity. Note: Do Not upgrade Ubuntu from the installed version as it will prevent EMC from working.

 [COLOR=White]///[/COLOR]______
< emc2 >
 [COLOR=White]///[/COLOR]---------
        [COLOR=White]............[/COLOR]\    ^__^
         [COLOR=White].............[/COLOR]\   (oo)\________
            [COLOR=White]................[/COLOR](__)\ [COLOR=White]..........[/COLOR]          )\/\
                [COLOR=White].....................[/COLOR]||-------w [COLOR=White].[/COLOR]|
                [COLOR=White].....................[/COLOR]||[COLOR=White]........; [/COLOR]         ||

                           [COLOR=White]....................................... emc2 >
 ------
        \   ^__^
         [/COLOR]

---

### Post by Rexhunt on 2009-12-22
Isn't EMC just a program to send g code to the machine? It doesn't actually produce the g code nessacery to control the machine.
 
Please correct me if I am wrong.

---

### Post by alexfish on 2009-12-22
> **Rexhunt said:**
> Isn't EMC just a program to send g code to the machine? It doesn't actually produce the g code nessacery to control the machine.
 
Please correct me if I am wrong.

Hi  

Are You Saying The Lathe Only Accepts Commands From Dos// As A File  . What is the name of the program  used on the Computer

   Which Type Of Controller Is On The Lathe

Need This To Find A Solution  /  See If There Are Any [ References  On The Machine] and the controller

You Can look 

Here
                                 

                                 Download information              
                                                **Basic installation**

             [SIZE=3][COLOR=Navy][Basic             Installation]("http://www.linuxcnc.org/content/view/21/4/lang,english/") from one of the EMC2 Live CD's is easier and             faster than ever. You can also try out EMC2 without installing             anything to your hard disk. [/COLOR][/SIZE]The EMC2 Live CD are based on **Ubuntu             6.06 "Dapper Drake" LTS** and **Ubuntu 8.04             "Hardy Heron" LTS** with additional packages             maintained by the linuxcnc development team.              

             Note: Do Not upgrade Ubuntu from             6.06 to 8.04 or upgrade from 8.04 to 8.10. The precompiled             versions of EMC2 are only compatible with the Ubuntu version they             were compiled with. Upgrading will remove the EMC packages and             make your system unable to run EMC.              
             With this configuration, you             continue to get all the benefits of Ubuntu, such as security             updates and excellent community-based support for the base OS,             plus support of the EMC2 components by the EMC2 team. (Ubuntu is             the preferred way to use EMC2).              

             **Other methods of installation**

             Other ways to obtain, compile, and             install emc2 are discussed on the community-maintained [linuxcnc             wiki]("http://wiki.linuxcnc.org/cgi-bin/emcinfo.pl?Installing_EMC2").
             **Source code**

             EMC2 is an open-source project.             Currently we keep the source-code in "Git" (a versioning             system) at [git.linuxcnc.org]("http://git.linuxcnc.org/").             You can browse the sources online, using [gitweb]("http://git.linuxcnc.org/gitweb?p=emc2.git;a=summary")             , or download them ([instructions]("http://wiki.linuxcnc.org/cgi-bin/emcinfo.pl?git")).
             
EMC"   [About]("http://www.linuxcnc.org/content/view/11/10/lang,english/")
            
[COLOR=Navy][COLOR=Black]EMC2[/COLOR]                 [Download]("http://www.linuxcnc.org/content/view/2/4/lang,english/")[/COLOR] 
             

[LIST]
[*][Documentation]("http://www.linuxcnc.org/content/view/5/5/lang,english/")
[/LIST]

               
[SIZE=3][COLOR=Navy] [G             Code]("http://www.linuxcnc.org/content/view/2/4/lang,english/")
[http://www.linuxcnc.org/docview/html/gcode.html](http://www.linuxcnc.org/docview/html/gcode.html)[/COLOR][/SIZE]                            
             

            [SIZE=3]
**[*EMC*             Documentation Wiki: EmcKnowledgeBase]("http://wiki.linuxcnc.org/")**

             [COLOR=Navy]Advanced examples of using *emc2*:             GcodeInfo - Things you might want to know about *G*-*Codes*;             Oword - *G*-*Code* Owords - loops, conditionals and             subroutines [B]...

[SIZE=2][COLOR=Black]Does The Machine Look Like The Screen Shot[/COLOR][/SIZE]
[/B][/COLOR][/SIZE]

---

### Post by alexfish on 2009-12-22
> **Rexhunt said:**
> Isn't EMC just a program to send g code to the machine? It doesn't actually produce the g code nessacery to control the machine.
 
Please correct me if I am wrong.

According to the documentation [SIZE=1]EMCO Compact 5 Lathe uses G Code ,so may be possible to use emc2  Compare the two Documents

[/SIZE][IMG]http://www.eric.ed.gov/ERICWebPortal/resources/images/btn_images/btn_icon_pdf.gif[/IMG] [ERIC                         Full Text]("http://www.eric.ed.gov/ERICWebPortal/contentdelivery/servlet/ERICServlet?accno=ED300589") (344K)                           

EMC2 Manual

[http://www.linuxcnc.org/docs/EMC2_User_Manual.pdf](http://www.linuxcnc.org/docs/EMC2_User_Manual.pdf)

THIS COULD BE AN [ INTERESTING PROJECT ] FOR THE UBUNTU FORUMS

**[SIZE=1][SIZE=2][COLOR=Navy]Using EMC  / Details [/COLOR][/SIZE][/SIZE]****[SIZE=1][SIZE=2][COLOR=Navy] Of A Retro fit [/COLOR][/SIZE][/SIZE]**[B][SIZE=1]

[SIZE=3][http://lerneaenhydra.net/compact5/](http://lerneaenhydra.net/compact5/)[/SIZE]


[/SIZE][/B]

---

### Post by patchwork on 2009-12-22
Are you trying to create a newer interface (similar to MAZcontrol), or are you trying to create g-code files to send to the lathe?

If you are trying to create the g-code files, I used to create g-code programs in any old text editor and send them out to a CNC VMC that was from around 1980.

If you are trying to create a GUI based system, I really don't have that kind of experience to help.

---

### Post by Rexhunt on 2009-12-23
I am trying to setup a new interface so that other people can easily use the lathe and so that we can use different tools to the ones preset in the origanal emco software

---

### Post by JoelOl75 on 2009-12-23
Sounds easy in theory, but unless you are a programmer AND have access to the lower level (usually RS-232) interface commands this isn't easily possible unless you have the source for the DOS program although this is not likely.

I program OMCG CNC wire bending machines at work and these systems use DOS and buggy Windows 3.11 for workgroups for a higher level "EZ program GUI".  The hard disk gets corupted all the time.  I had the idea of using linux just for a better filesystem (With maybe wine for the GUI program)and possibly using just 1 computer to run all four machines with redundant power supplies and RAID1 to make them rock solid...  I'd love to be able to re-write the GUI program using some high level language even.  It would be easy to implement some features we'd like to have and remove stuff we never use.

But....  The interface is serial and the software is locked to the each machine with a parallel port dongle.  It maybe possible to see exactly how this dongle works, but then still, the closed nature of this proprietary software turns it into a bus sniffing and reverse engineering project... WAY over my head.  If these companies didn't lock the machines with a dongle and supplied the source and maybe an API I can imagine the possibilities.  It shocks and confuses me why they do this!!!  Their software sucks and has so many bugs and the company bought the machine anyway that opening the software under a GPL or even BSD license would further enhance the machine with community contribution and possibly net them much more sales of the machines.

OMCG of Italy.... You suck!

---

### Post by Rexhunt on 2009-12-23
I have seen on the internet somewhere someone has connected up this lathe to a machine running windows xp. However they had to actually bridge an ic on the lathe to eradicate the need for an extra signal not sure what the signal is for though.
 
This is a possibility but I would much prefer it if I could avoid doing that.
 
This is a main reason for me turning to linux. Because even if the software didn't provide the extra signal then a program could be made to take the output of the progam and add the extra signal, or even modify the program

---

### Post by alexfish on 2009-12-23
> **Rexhunt said:**
> I have seen on the internet somewhere someone has connected up this lathe to a machine running windows xp. However they had to actually bridge an ic on the lathe to eradicate the need for an extra signal not sure what the signal is for though.
 
This is a possibility but I would much prefer it if I could avoid doing that.
 
This is a main reason for me turning to linux. Because even if the software didn't provide the extra signal then a program could be made to take the output of the progam and add the extra signal, or even modify the program

Hi

 [SIZE=2]There Is A Site Here

You would need to Buy An   [/SIZE][SIZE=1][SIZE=2]WELturn 5 PC Controller

  + the Software

[http://www.welsoft.co.uk/welturn.html](http://www.welsoft.co.uk/welturn.html)

Did You Have A look At Details Of the Retro fit As mentioned above For Using Emc linux  . if you look carefully on the site there is a link for the For details of  "Pin inputs ect"



[/SIZE] 
[/SIZE]

---

### Post by Rexhunt on 2009-12-23
So for that system all the modifacation I would have to do is unplug the computer and plug this in between the lathe and the computer?
 
This would work, because it is only cables and computer that have been changed so if worst comes to worst the we could just go back to the old computer.
 
Thanks.
 
I will let you know if it works after school starts.

---

### Post by alexfish on 2009-12-23
> **Rexhunt said:**
> So for that system all the modifacation I would have to do is unplug the computer and plug this in between the lathe and the computer?
 
This would work, because it is only cables and computer that have been changed so if worst comes to worst the we could just go back to the old computer.
 
Thanks.
 
I will let you know if it works after school starts.

There Is A Live Cd Available Pre Compiled With EMC2 Here  , it is Base On Ubuntu 8.04 


[LIST]
[*][download the ISO]("http://www.linuxcnc.org/hardy/ubuntu-8.04-desktop-emc2-aj13-i386.iso") ([EU mirror]("http://dsplabs.upt.ro/%7Ejuve/emc/")) and burn it to a CD. (The MD5SUM of the CD is 1bab052ec879f941628927c988863f14)
[/LIST]

---

### Post by Thelasko on 2009-12-23
If you want to do CNC you need to learn G-code.  End of story.  When I was in engineering school (4 years ago) I learned G-code.  We had an old DOS machine too, and it worked fine.  I'm not aware of a CNC machine that doesn't use G-code.

I am aware of a plugin for Unigraphics that will generate the G-code from a solid model automatically.  That software costs thousands of dollars, and I doubt there is an open source alternative.  Not to mention you need a *very* fast computer to run it.

Either way, the user of the CNC should know G-code.  At least to make sure the code is correct.  You run it with too high of "feed" and not enough "speed" and you have an expensive mess to fix.

I'd stick with the DOS machine myself.  Learning to use it should be part of your educational experience.

---

### Post by Rexhunt on 2009-12-23
I understand where you are coming from and agree learning g code is an important component of this project however there is no one that I know who can program and then teach me.

On the dos computer I have no real problem with using it except for the fact that we don't have the origanal tools and the software does not support using different tools. The other problem is that as far as I know no one in the school is comfortable with a dos interface, and I would like to know that when I finish year 12 it will not lay idle for the next 15 years before it is thrown out due to an outdated interface that no one knows how to use any more.

---

### Post by Rexhunt on 2010-01-09
Check this out.
 
[http://finance.groups.yahoo.com/group/Emco_cnc_users/](http://finance.groups.yahoo.com/group/Emco_cnc_users/)
 
You may have to register though, it is free.

---

### Post by Rexhunt on 2010-03-12
Ok I see that no one else has posted here, but still...
 
Does anyone know what numbers I need to feed into EMC to work with the EMCO lathe?
 
And is there anyone experianced with EMC and can tell me how to import an image to a lathe?

---

