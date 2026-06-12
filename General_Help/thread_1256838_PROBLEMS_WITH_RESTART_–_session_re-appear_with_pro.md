---
title: "PROBLEMS WITH RESTART – session re-appear with problems"
date: 2009-09-03
forum: General Help
---

### Post by lafadnes on 2009-09-03
[FONT=Arial][SIZE=2]After a week as happy and enthusiastic Ubuntu user with hardly any problems at all, I have got a problem which I find difficult to solve:

[/SIZE][/FONT]    [FONT=Arial][SIZE=2]As I start the machine, all the programs from the previous session are open (just like hibernate in windows) even though I have chosen Shut down and Restart with several restarts. This worked very well earlier with a normal shut-down (until I installed the [/SIZE][/FONT][FONT=Arial][SIZE=2]xfce4 [/SIZE][/FONT][FONT=Arial][SIZE=2]which may have caused the problem. I have also removed the tick of 'Automatically remember running applications when logging out' in the ' Startup Application Preferences'[/SIZE][/FONT]
  [FONT=Arial][SIZE=2] [/SIZE][/FONT]
  [FONT=Arial][SIZE=2]This seems to give me several functional problems including problems with links, library information etc.[/SIZE][/FONT]
      [FONT=Arial][SIZE=2]  
[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]1. Several links seems to be broken, e.g. the following message:
[/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT][FONT=Arial][SIZE=2][/SIZE][/FONT]  
  [FONT=Arial][SIZE=2]The Link "Link to Forskning" is Broken. Move it to Trash?[/SIZE][/FONT]
[FONT=Arial][SIZE=2] 
[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]This link cannot be used, because its target "/media/DATA/Forskning" doesn't exist.[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]Cancel        Move to Trash[/SIZE][/FONT]
    [FONT=Arial][SIZE=2] [/SIZE][/FONT]
  [FONT=Arial][SIZE=2]2. The [/SIZE][/FONT][FONT=Arial][SIZE=2]TomboyApplet seems to have problems and this message now appears in every start-up:
[/SIZE][/FONT]
  [FONT=Arial][SIZE=2] [/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] [FONT=Arial][SIZE=2]Error[/SIZE][/FONT]    [FONT=Arial][SIZE=2]The panel encountered a problem while loading "OAFIID:TomboyApplet".[/SIZE][/FONT]
   [FONT=Arial][SIZE=2] [/SIZE][/FONT]
   [FONT=Arial][SIZE=2]Do you want to delete the applet from your configuration?[/SIZE][/FONT]
      [FONT=Arial][SIZE=2]Don't delete        Delete[/SIZE][/FONT]
 [FONT=Arial][SIZE=2] [/SIZE][/FONT]
      [FONT=Arial][SIZE=2]3. Amarok has forgotten its library collection (and is not able to re-locate the music library which is in another folder than the standard folder [which did not cause problems at all earlier])
[/SIZE][/FONT]
[FONT=Arial][SIZE=2]
If you have some good advices I will be very greatful! I am really enthusiastic about the Ubuntu!
Lars
[/SIZE][/FONT]

---

### Post by P4man on 2009-09-03
can it be all these problems relate to the same thing: a drive that isnt (yet?) mounted? Is "/media/DATA/Forskning" by any chance an ntfs volume that you use to store your music on?

---

### Post by lafadnes on 2009-09-03
This may be true, but I find it strange that it has been working well for many days.
Both the links and the music is located on the D:/ drive.
The TomboyApplet for writing notes does not involve the D:/ drive though.

How can I solve the problem if this is the case?

---

### Post by lafadnes on 2009-09-08
[FONT=Verdana][SIZE=2]After mounting the drive permanently it now works well!
[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Thank you very much![/SIZE][/FONT]

[SIZE=2]I got some goods tips on how to mount the a drive permanently in the following website which can be warmly recommended:
[/SIZE]
[FONT=Verdana][SIZE=2]http://www.psychocats.net/ubuntu/mountwindows
[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]

---

### Post by egalvan on 2009-09-08
> **lafadnes said:**
> 

[SIZE=2]I got some goods tips on how to mount the a drive permanently in the following website which can be warmly recommended:
[/SIZE]
[FONT=Verdana][SIZE=2]http://www.psychocats.net/ubuntu/mountwindows
[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]

Absolutley +1 for psychocats, it's an excellent piece of work.

Also try herman's web page, hermanzone.

---

