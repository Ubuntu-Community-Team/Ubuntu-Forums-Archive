---
title: "Kmail not reciving POP3"
date: 2006-06-20
forum: General Help
---

### Post by Cbertram68 on 2006-06-20
I installed Kontact, (becasue I like the journaling feature) and most of the other components such as Kmail, but I am getting an error about pop3 not starting.  I use Yahoo as my gateway.  pop.mail.yahoo.com
 
I had Mepis installed before switching to pure Ubuntu because I like Gnome better than KDE, and it is lighter than Mepis, but I had no issues with Kmail then (my issue then was CUPS/SMB printing).
 
I know I may have an issue with SMTP, because Yahoo sometimes uses an alternate port, but they do not do that for pop3.  I can ping the pop3 server, and would like to get it working.
 
FYI: Evolution is using the same settings and is able to get the mail just fine.  Is there a possible conflict between Evolution and Kmail?:confused: 
 
Thanks for any help.](*,)

---

### Post by bruce89 on 2006-06-20
Why would you use Kmail in GNOME though?  If you don't like evolution, then use thunderbird.

---

### Post by Cbertram68 on 2006-06-20
[quote=bruce89]Why would you use Kmail in GNOME though? If you don't like evolution, then use thunderbird.[/quote]
 
To answer your "Answer"? I have never tried Thunderbird.  
 
I used Kontact and Kmail in Mepis, and I liked the look and feel of it, and as I stated before it has a very cool journaling (kind of like a diary) feature.  I am an Ex-Franklin Planner user and like to keep a journal of my days events.  I understand that it is a KDE program, Kontact seems to work quite well, it is only Kmail that is not working.
 
The problem with the rest of your answer is that you do not tell me whether Thunderbird has the features that Kontact has.  I am perfectly willing to give it a try, but the one feature I am looking for is the journaling feature, email, address book, calander, and todo list are available in most PIM's.  So is journaling available in Thunderbird?

---

### Post by Caveira2099 on 2006-06-21
Hi, I am having the same problems here!

I had only KDE until dapper release, and I really needed my old e-mails... I can read them in kmail, but not use it. Evolution seems to be working fine, but I prefer a program that allows me to receive mail directly to specific (and different) folders, because I work with 6 e-mail accounts...

I any1's got any ideas, please post!

[]'s

---

### Post by Cbertram68 on 2006-06-22
I am still haveing the same issue, I am gload that I am not the only one who would like to use Kmail in gnome.  I will post agin if i find an answer.

---

### Post by Cbertram68 on 2006-06-22
This may not be the answer, andI can not test until I get home.  THis post was about a KDE install of Firefox, that when the user clicked on an email address it would open Evolution.  THe user wanted it to open Kmail.  At any rate, this might be a possible path to check out.
 
[COLOR=lime]It sounds like KDE treats KMail as the default mail client, but Firefox isn't aware of that because it's a GTK app. To get it to use KMail, you'll have to set the default mail client in the Gnome control center.
If you don't have a menu entry for Gnome control center, you can bring it up from a terminal by typing gnome-control-center <Enter>. Then double-click on "Preferred [/COLOR][[COLOR=lime]Applications[/COLOR]]("http://www.linuxforums.org/forum/#")[COLOR=lime]," and the rest is cake.[/COLOR]
[COLOR=lime][/COLOR] 
[COLOR=black]If this user had an issue with using Kmail as default in KDE, then maybe we are having an issue using Kmail as default in Gnome?[/COLOR]

---

### Post by Cbertram68 on 2006-06-22
I want to move this thread to Desktop Support.  So if an moderator can do that it would be great, otherwise I am starting a new thread in Desktop support.

---

### Post by Caveira2099 on 2006-06-22
Well, I've just tried this suggestion, but nothing new... "Can't start pop3" appeared again <sigh>

Let's see if any answers come. I am searching for one too, but found nothing until now...

---

### Post by Cbertram68 on 2006-06-22
I have been searching everywhere as well, I went to kmail.kde.org, and tried to search there.  Nothing.  The thing is that I have read that it should work in several different posts, and one other interesting thing I found was that we may need to load KDEPIM, and any requirments.  I have to get all my repositories set up so I can find that.  I will post again when I get home and have a chance to do that.

---

### Post by Cbertram68 on 2006-06-23
Well I went home last night, and tried everything I could think of, and could not get it to work.  So for now I am going to go with Evolution, at least until I can find something like the KDEPIM that will work for me.

---

### Post by benmoreassynt on 2006-07-07
I have the same problem. I used to have both Kubuntu and Ubuntu installed on a previous computer. At that time KMail worked fine in Gnome. But I have given up on Kubuntu on a new computer - but I like KMail.

The fact that it does work when Kubuntu/KDE is fully installed suggests that there is a dependency that is not being installed by Synaptic that is necessary to make the pop3 connection work. Does anyone know what this might be?

---

### Post by Cbertram68 on 2006-07-07
[LEFT]I was just reading on TUX Magazine a story from last March I believe, and the guy said that Kontac/Kmail will run under Ubuntu, but that you need to have the KDE desktop installed, you don't need to run it, but it needs to be installed.  SO you are right there seems to be a dependency on KDE, but what exactly it is is a mystery.](*,) [/LEFT]

---

### Post by benmoreassynt on 2006-07-07
That's a shame - I don't really like Evolution, and Kontact has loads of good features - especially the built in RSS reader. But is seems silly to install KDE just for that. It would be worth someone working out what needs to be included, as it is a very good standalone application.

---

### Post by Cbertram68 on 2006-07-10
[LEFT]I agree, so I went to Kubuntu, then found I was having other issues, and installed Mepis on top, I now have MepUntu.  My laptop is running very well now, and I am very happy with it.  Good luck on finding an answer to wht the dependencies are.
 
One other thing I did not check, when I was in my MepUntu, and I did the upgrade to all packeges, I found that Gaurd Dog was running, and it actually broke Kmail from sending.  I am not sure if there is a firewall in Ubuntu, but you might check those setting as well.  It is the one thing I did not think about until later.[/LEFT]

---

### Post by mike78_at on 2006-08-08
Hi Cbertram68,

no you are not the only one wanting to use kmail on Ubuntu. I had the same problem as you and have solved it the following way: first you need the kdepim-kio-plugins installed and second the kdebase-Package (with all automatically included dependencies). As for the kdebase-Package I assume that all you really need is the kdebase-kio-plugins but I already pulled in the whole kdebase-package and don't want to sort all things out again! Maybe you could tell us if kdepim-kio-plugins and kdebase-kio-plugins alone do the trick!

Greetings,

Michael

---

### Post by Robert Leithe on 2006-08-13
Although I'm not 100 % sure, this sounds exactly like the same problem I faced when I installed Ubuntu and KMail recently.

In a Norwegian linux forum I received this suggestion (translated into english):
"I think installing kdebase will solve this problem.
Try this command line:
sudo apt-get install kdebase


and see if that doesn't work for you"

I tried, and it solved the problem for me.

Robert

---

### Post by Jheric on 2006-08-13
There is definately a dependancy some dependancy in kdebase. I installed EVERY pim related kde package with no sucess. Then I installed kdebase and "bingo", everything works fine.

I know a lot of gnome pros think this is stupid but the truth of the matter is: K-apps are very good. For a PIM guy, like myslef, Kontact is the only real option (I was on Franklin planplus in windows... a special version of Outlook). So far no player really challenges Amarok imho. I take these apps with me no matter the distro cause they just rock.

-Garrett

---

### Post by Salim on 2006-09-10
I had this same problem. I used MEPIS first and now changed to Xubuntu. So I've copied my kde files, mail directory, *rc files and so on.
KDE-Applications are great. I especially like Kontact (with KMail, Korganizer, and so on) and AmaroK. They rock :-)
Reading this post finally solved my problem. The package "kdebase-kio-plugins" solved the issue.

---

### Post by rusyear04 on 2006-11-17
hi there, :cool:

i had the same problem after adding **Kontact**to my **gnome**ubuntu (edgy eft).

recieved the error:
```
Could not start process pop3
```
at startup of **Kontact**.

solution for me:

```
sudo apt-get install kdebase
```

works fine now ;)
although i'm a Linux-newbie, so i have no clue if there are more elegant solutions (this one requires some 70MB of disk-usage). :-k 

well, i'm happy to have found a PIM that works (so far :p )

---

### Post by talkaboutquality on 2007-09-24
> **Salim said:**
> I had this same problem. I used MEPIS first and now changed to Xubuntu. So I've copied my kde files, mail directory, *rc files and so on.
KDE-Applications are great. I especially like Kontact (with KMail, Korganizer, and so on) and AmaroK. They rock :-)
Reading this post finally solved my problem. The package "kdebase-kio-plugins" solved the issue.

Same worked great for me. Only 3MB extra! :)

I chose Kmail because of its easy import from Outlook Express (I got rid of Windows after the umpteenth problem with it).

---

