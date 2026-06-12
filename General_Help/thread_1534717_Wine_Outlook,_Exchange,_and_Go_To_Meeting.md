---
title: "Wine Outlook, Exchange, and Go To Meeting"
date: 2010-07-19
forum: General Help
---

### Post by danrche on 2010-07-19
Does anyone know of any "Wine" goodies that can get outlook 2007 running on exhcnage 2007? I know about running windows in a vm but I'd like to get it running natively. Any suggestions? 

I know about Exchange's OWA being a complete re-write, but I didn't know if anyone had solved this. 

My other question is can I attend go-to-meetings in linux? and if so how? I've only seen this work on windows with active x plugins.

---

### Post by danrche on 2010-07-22
well, here's what I've figured out: 

No, OWA or Rpc/https will not work with Outlook and wine on exchange 2007 but will work just fine on exchange 2003. 

Outlook 2007 and exchange 2007 will connect within the network (so when you're at the office). and all functionallity seems to work just fine. 

Go To Meeting - doesn't support linux at all. still stuck with Microsoft :( 

it seems these days simply having an opensource alternative doesn't matter. If you can't use the specific tools laid out in MS world, you're loosing out.

---

### Post by SaintDanBert on 2010-08-06
If I have **wine** with **internet explorer** running, can I connect to "Go To Meeting" presentations?

~~~ 0;-Dan

---

### Post by spawnywhippet on 2010-09-07
> **danrche said:**
> well, here's what I've figured out: 

No, OWA or Rpc/https will not work with Outlook and wine on exchange 2007 but will work just fine on exchange 2003.

Would you mind sharing what you learnt about how to configure Outlook 2007 to talk to Exchange over https? I have already installed it, but can't get it to talk to Exchange.

(I'm a Linux newbie, so am not familiar with crafting my own orders on the command line)

---

### Post by danrche on 2010-09-07
So far with Wine and exchange 2007 I have been unsuccessful in connecting via Https. I am using it local to the Lan, but not outside of it. I can connect to exchange 2003 via rcp/https, but most IT shops have already upgraded. I believe there may be a way to connect outlook to exchange 2007 https in wine if you install the correct MS components, but I don't have any list as of yet. I will continue to work on it and will let you know. 


Currently I'm viewing email in a virtual xp box running outlook. :(  

As for the go-to-meeting, I can view them in a virtual box running xp, but nothing for linux. I did see some post from employee's of go-to-meeting who are begging for a linux install, but as of yet, none seem to be available. Best of luck to you if you're just starting out, I seem unable to break from windows completely, but can't seem to go back to it either.

---

### Post by PerfectReign on 2010-10-04
I've never been able to get Outlook 2007 working. 
I have excel running just fine as well as Word. (In fact, Word 2007 is still faster running under Wine than is OpenOffice.)
 
I ran winetricks to load files, but get a funky error message at the end.
 
In any case, here's what I get trying to run Outlook 2007.
 
 
 
As for GoToMeeting, I can run the download file, which then downloads an installer. This then gets a bunch of errors in assemblies and whatnot...
 
 
[FONT=Arial][FONT=Courier New][SIZE=2][COLOR=red]kai@kai-laptop:~$ env WINEPREFIX="/home/kai/.wine" wine start /Unix /home/kai/.wine/dosdevices/c:/windows/profiles/kai/Start\ Menu/Programs/Microsoft\ Office/Microsoft\ Office\ Outlook\ 2007.lnk
err:process:start_wineboot failed to start wineboot, err 11
fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:exec:SHELL_execute flags ignored: 0x00004100
kai@kai-laptop:~$ err:module:import_dll Loading library credui.dll (which is needed by L"C:\\Program Files\\Microsoft Office\\Office12\\OUTLOOK.EXE") failed (error c0000020).
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Microsoft Office\\Office12\\OUTLOOK.EXE" failed, status c0000135[/COLOR][/SIZE][/FONT][/FONT][FONT=Times New Roman][/FONT]
 
 
 
...followed by a "GoToMeeting failed to start, or exited with an error. Please try again." message.
 
 
[IMG]http://www.perfectreign.com/stuff/2010/goto_meeting_wine.png[/IMG]

---

### Post by danrche on 2010-10-05
excellent post, PerfectReign. 

You may need to install some extra's to get it going, here's what I've got on my bottle with Office 2007

windows installer 2.0 redistributeable, sml parser (MSXML) 3.0, Visual C++ 2005, .net framework 1.1, XML Parser

Hope this helps


that's interesting that MS Office runs better then openoffice. I don't have any trouble with my OpenOffice and I use it in place of office only relying on MS Office when I absolute need to (to check the format before sending out to a customer).

---

### Post by danrche on 2010-10-05
> **SaintDanBert said:**
> If I have **wine** with **internet explorer** running, can I connect to "Go To Meeting" presentations?

~~~ 0;-Dan

sorry dan, doesn't look like you're going to be able to do this as GO to Meeting is looking for some MS plugins to work.

---

### Post by fore_perry on 2010-10-12
[COLOR=black][FONT=Verdana][FONT=Book Antiqua]Man am I glad to see this post!!!  I was being to think that I was the only one having issues getting Outlook 2007 to work.  Would you mind telling me what it is that you see when you load Outlook in Wine?  I am very new to Ubuntu (This is my first install) and I am thinking that I am not as familiar with Windows as I thought...  not sure what the OWA or Rpc stand for... I really want to get away from Windows so bad I can taste it! (so that is my story)[/FONT][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][FONT=Book Antiqua]Here is the short version of my issue.[/FONT][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][FONT=Book Antiqua] [/FONT][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][FONT=Book Antiqua]Outlooks seems to load just fine, untill it is time to install my configuration information.  All of the screens are blank! No area to input any information.  Does this sound like anything you have seen?[/FONT][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][FONT=Book Antiqua] [/FONT][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][FONT=Book Antiqua]As for Word, Excel, PP, Visio all seem to be running just fine. (I just got them installed today)  I was a little scared when it took 2+ hours to get Excel to finally work...  Even the app killer did not seem to shut it down (good thing I guess).  Any issues that I should be aware of before I start using it all of the time?[/FONT][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][FONT=Book Antiqua] [/FONT][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][FONT=Book Antiqua]Guys I would greatly appreciate any information  [/FONT][/FONT][/COLOR]
[FONT=Book Antiqua][SIZE=3] [/SIZE][/FONT]

---

### Post by danrche on 2010-10-12
fore_perry,

Best advice for you $50 for Crossover by CodeWeavers will solve your issues all together. I worked with one of my customers on it and had him buy the pro version and it's WONDERFUL!!! If you can afford to shell out the bucks it's worth it not having to trouble shoot all the issues within Wine.

With that said, have you loaded msxml3 and 6 and .net framework 1.1 into your wine bottle? What version of Wine do you have installed? What version of Office are you using?(I know your on 2007, but which one, retail, pro, etc....).

---

