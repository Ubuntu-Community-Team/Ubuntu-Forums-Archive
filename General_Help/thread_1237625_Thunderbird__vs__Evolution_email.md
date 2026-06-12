---
title: "Thunderbird  vs  Evolution email"
date: 2009-08-11
forum: General Help
---

### Post by trixman on 2009-08-11
a friend of mine is torn between which email program to use on her linux ubuntu system.

its between "Thunderbird & Evolution "

she might lean towards Evolution because it came pre loaded, she is not sure what to pick, are they both solid to use.

thanks to all

---

### Post by rifak on 2009-08-11
i used evolution when i first started using gnu/linux but eventually switched to thunderbird. id suggest thunderbird

---

### Post by fballem on 2009-08-11
I first used Thunderbird and switched to Evolution. There are three primary reasons for me:

1. Evolution is integrated with GNOME, so if I set up a reminder on a calendar entry, the clock with the reminder will show on my GNOME panel, regardless of whether or not Evolution is actually running at that time.

2. The tool is most similar to Outlook, which I got comfortable with in Windows.

3. The data is easy to backup and restore. The built-in backup in evolution creates a tar.gz file that can then be copied to external medium - like a usb disc. If I need to restore the system, then when I first open Evolution, I have the option to restore from a backup, which will bring back all of the e-mails, calendar entries, accounts, and settings (except passwords) that were included on the backup. I generally make a new backup every couple of days.

A lot of the choice will depend on what is it that your friend needs and what she is coming from. In my case, I needed the local e-mail and calendaring functions and I came from Outlook. The simple backup was a bonus as was the alarm for calendar entries without having to keep Evolution running.

Hope this helps,

---

### Post by amdemas on 2009-08-11
Both are great email clients. I personally have been using thunderbird for some time now. I had used evolution with linux distros. Though when i switched to Ubuntu 9.04 i noticed that evolution was pre installed like you stated. I still found Thunderbird to be the best. In a Gnome aspect Evolution is better. Yet if you have multiple computers and not all of them are Ubuntu then Thunderbird is better. Still i am basis towards thunderbird. 


:guitar:

---

### Post by solitaire on 2009-08-11
I used Evolution when i first started using Ubuntu 6.04. but there was an issue with evolution not clearing out mailbox's when using POP3 boxes. they got full and people started to get bounces...

I had to empty my isp's mailbox manually.

Not tried it lately, but i'm finding i need to use the calendar more so might try Evolution again when 9.10's released.

Anyone know a good way to transfer emails between thunderbird and evolution??  lol ^_^

---

### Post by fballem on 2009-08-11
> **solitaire said:**
> Anyone know a good way to transfer emails between thunderbird and evolution??  lol ^_^

It's been a while, but both use mbox format. When I first converted from Thunderbird to Evolution, I:

- made a copy of the mbox files (the ones without extensions) from my Thunderbird folder. I think these are located in a folder under the profile folder within the .mozilla folder.
- started evolution and set up a local host email (username@localhost). This will create the necessary folder structure in the .evolution folder. Specific values around pop and smtp can be anything, but the email address must be 'username'@localhost, where 'username' is your username (without the quotes). In my case, for example, I would use fballem@localhost.
- exit Evolution, then locate the folders. ~/.evolution/mail/local.
- delete Inbox and Sent (these are the mbox files).
- copy the mbox files that you had saved in Thunderbird to the ~/.evolution/mail.local folder
- ensure that the sent items mbox is named 'Sent'. If necessary, you may need to rename the sent items mbox from Thunderbird.
- open Evolution - your e-mail should now be transferred. It may take some time for all of the folders to refresh.
- when done, delete the username@localhost account and set up your real e-mail accounts.

Hope this helps,

---

### Post by enlli on 2009-08-11
Thunderbird because with Lightning it has a better implementation of Google Calendar. Evolution can't handle repeats

---

### Post by solitaire on 2009-08-11
> **fballem said:**
> It's been a while, but...

Thanks. Will have to try it out..

@enlli

I've only found out a bout lightning a few months ago. Really useful! ^_^

---

### Post by fballem on 2009-08-11
> **enlli said:**
> Thunderbird because with Lightning it has a better implementation of Google Calendar. Evolution can't handle repeats

Evolution handles repeats quite well - as shown on the attached screenshot.

Hope this helps,

---

### Post by credobyte on 2009-08-11
Evolution just because it's similarity to Outlook ( tasks, calendar, etc. ).

---

### Post by Tclarkie on 2009-08-11
Thunderbird all the way

---

### Post by zotrules on 2009-11-01
yeah... I agree to most of the comments here...
I'd strongly say that thunderbird stays a lot higher comparing to evolution, and i mean it. But i'll let you into something that might sound strange... I've almost never used evolution. The reason? Because i tried, and i tried so hard to set up an email account with it, that i simply had to give up and discard it as a program. I've had used thunderbird before, seamonkey, mozilla suite, they're all the same regarding the email client; very easy to use, very easy to set up, very easy to migrate, very easy to export and import between them or other mail clients. It just isn't the case with evolution. There was no import anything from an existing mail client in my ubuntu...  i simply had to try to set it up from the very start; but i just couldn't!!! For some reasons, i did evrything perfectly right, still, evolution wouldn't connect at all to my mail server.
I tried with yahoo and this email provider: [www.gawab.com](www.gawab.com). It's the easiest email account you can set up after gmail, but with gmail, most email clients are  pre set up to accept settings by default and go automatically all the way to the end if you only know your email address and password. 
To be completely fair, i only wanted to use evolution because it comes integrated with ubuntu. This is the only reason that pushed me to try it. But the headaches to set it up, pushed me further away from it. I simply don't care at all if it has some calendar or address book... completely useless features for me... an email client that actually did work, sent or received email, that is the most important thing you'd expect from a mail client.
Now it comes to another concern of mine... the buzzkill with all this myriads of programs that do the same thing! An immense choice opportunity... this is way, way more than internet needs. Just as it comes up to ubuntu per se, tons of programs that do the same thing and most of them do nothing you'd need them to do.
I mean, "Empathy" for a start... what is the need for a program like that? it is the time when it's extremely harder to find a laptop without an integrated webcam, no matter what, webcams have been around fashionably for some 10 good years (a lot lot more, but let's say 10), what is the need for a program like "Empathy" when you can't have a videocall or make use of a webcam??? The tragic thing is that it comes perfectly integrated with karmic, just as pidgeon used to be with jaunty... none of them supports a webcam. This is just a shame and a waste. Now to avoid all misunderstandings, i like them as programs for what thy do, but they're simply useless for the time we live in. They impoverish Ubuntu or other linux systems. 
If this were a kind of competition between operating systems, i could understand why Windows beats linux almost and always in every aspect.
Why should someone have second thoughts after trying Ubuntu/migrating from windows? I just can't understand the titanic work the ubuntu guys do to keep up with it, and they fail just for some simple but indispensable features; like the features of communicating between platforms and systems. Understandably, it has been impossible to send a picture from pidgin to windows live messenger, or receive one; the same with amsn, emmesene, and i will just have to wait to see what empathy can do...
till now, i've had second thoughts even because i couldn't fix a simple device on top of my laptop screen called a webcam, that ubuntu feels so spiteful about. Obviously i almost came to the conclusion that unless you're a programmer yourself, linux systems are as friendly as the number of times ubuntu would ask you for a password, although you've logged in a thousand times and although you are the only administrator, even a better administrator and more alive than "root" or "sudo" or "gksu".
Anyway, for friendliness, better usability, better robustness, simplicity, i would choose thunderbird over evolution one thousand times.

---

### Post by scouser73 on 2009-11-01
I've never used Evolution since I made the switch to Ubuntu, but here's why I think Thunderbird is the est email client.

Thunderbird 3 beta 4 now has tabs, yes I'm talking about a beta release which I know many people won't use as a primary client. I like the fact you can have addons for it (I'm unsure if this is possible with Evolution) and also themes.

In my opinion I think Thunderbird should be the default email client for it's overall ease of use and appearance to the eye.

---

### Post by RJ12 on 2009-11-01
> **zotrules said:**
> ...Obviously i almost came to the conclusion that unless you're a programmer yourself, linux systems are as friendly as the number of times ubuntu would ask you for a password, although you've logged in a thousand times and although you are the only administrator, even a better administrator and more alive than "root" or "sudo" or "gksu".
Anyway, for friendliness, better usability, better robustness, simplicity, i would choose thunderbird over evolution one thousand times.
This happens in Vista and 7. The reason in Ubuntu/Linux is if there was ever a virus to get in ubuntu (not likely though) you would have something randomally ask for a pass. Also to me it serves as a warning to me it says "You are about to change something that could impact the usablility of your system if you would like to continue please type your pass and press enter"

On Topic: I dont know which I would choose probally Evolution as its preloaded for a reason and one of them is its intergrated in Gnome. For those who have a groupwise account it also has that capability (I forgot does tb have this?)

---

### Post by RJ12 on 2009-11-01
> **scouser73 said:**
> I've never used Evolution since I made the switch to Ubuntu, but here's why I think Thunderbird is the est email client.

Thunderbird 3 beta 4 now has tabs, yes I'm talking about a beta release which I know many people won't use as a primary client. I like the fact you can have addons for it (I'm unsure if this is possible with Evolution) and also themes.

In my opinion I think Thunderbird should be the default email client for it's overall ease of use and appearance to the eye.

You have a really good point and should be considered by the OP

---

### Post by zotrules on 2009-11-02
> **RJ12 said:**
> This happens in Vista and 7. The reason in Ubuntu/Linux is if there was ever a virus to get in ubuntu (not likely though) you would have something randomally ask for a pass. Also to me it serves as a warning to me it says "You are about to change something that could impact the usablility of your system if you would like to continue please type your pass and press enter"
Fortunately, or unfortunately,- take it as you please, it doesn't happen in 7 anymore. That deadly annoyance ended with vista. While 7 recognizes the user privileges as you log into the system. I've used it for a couple of days now, and it not only looks great, it behaves great too. I am not against security, but that should be more up to the user to decide whether he/she can take it and face the same refrain over and over again every day, a thousand times a day... There's no practical option or user-iterfaced module in Ubuntu (karmic) so far to get you to this process. So, unless you're a programmer and have time to waste to rake within forums in the internet, then Ubuntu IS NOT the environment you'd like to have for everyday use. It has lost a lot of friendly features and customizability. Just as what happened to me yesterday; thought to give a try to xubuntu environment... so I installed the environment... somehow, i lost a lot of features from the gnome environment. And even now, after i uninstalled xubuntu environment, i simply can't get them back. It certainly wasn't as much the case with jaunty as it is with karmic.
Now, i know, it is a free operating system, and i think the job done is marvellous. I don't reproach almost nothing at all, but certainly, i choose to write because i think it can get better, and it can get a lot lot better. there's plenty of room for improvement, and comments like mine should be considered in this angle only.
Just go and visit the bugs site... almost all of them state "resolved" and "patch available in the repositories"... but nothing comes around as such. So, we are facing some serious problems here.
Nevertheless, i stand firm on what i've said in my previous comment.

---

### Post by hades_6_6_6 on 2009-11-03
I'm using Thunderbird for years and really appreciate it, but as I've just installed Karmic from scratch, I've decided to give Evolution a chance. However Evolution is a good email-client and has a better Ubuntu integration (GNOME, Ubuntu One, etc), I've switched back to Thunderbird after a couple of days. I was missing following features.
- Ability to have separate folders (Incoming, sent, etc) for each email account.
- Keep a copy of the email on the POP3-server BUT delete if if you delete it in the client

---

### Post by finno on 2009-11-04
I have been unable to get Thunderbird working with Karmic due to problems outlined here [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/431091](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/431091). I have been unable to get Evolution working either - unable send mail via SMTP.

---

### Post by zotrules on 2009-11-04
> **finno said:**
> I have been unable to get Thunderbird working with Karmic due to problems outlined here [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/431091](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/431091). I have been unable to get Evolution working either - unable send mail via SMTP.
Why not try to reinstall karmic? I suppose some missing repos could have already been included in the main release. Still, like i said before, from intrepid or jaunty, karmic is a wholesome downgrade, it is exactly what i didn't expect, although, the same lovely.

---

### Post by Visible Spirit on 2009-11-04
**Hi trixman**,


I personally recommend Thunderbird for your friend. It's a cross platform email client that once your familiar with, can be used on virtually *any* popular OS. Imports and exports emails easily. It's highly customizable with [add-ons]("https://addons.mozilla.org/en-US/thunderbird/") just as the Firefox browser is. Emails can be encrypted via OpenPGP through the use of [Enigmail]("https://addons.mozilla.org/en-US/thunderbird/addon/71")-(point-n-click setup of certificates etc.once installed). Each email account you setup has it's own folders so there's never any confusion regarding which email is from which account. The filtering capabilities for searching through your emails are superior to any other client I've tried-(and I've tried a few of 'em). It has tagging via categories and custom colors making emails easy to ID for various quick searches of tagged individual emails or email groups.

If you need calendar scheduling and To-Do lists, [Lightning]("https://addons.mozilla.org/en-US/thunderbird/addon/2313") offers the option of publishing either to an on-line schedule server or marking them private-(amongst other categories of choice), with custom categories and one time or multiple/repeating reminders. Thunderbird also allows you to create custom named folders/directories under the local folder tree with sub folders to organize and categorize your saved/archived emails. I could go on forever about the features and customization abilities of Thunderbird that no other email client offers or compares with.

The Lightening add-on linked above offers a sidebar to list your events and/or To-Do lists with mouse-over pop-ups showing your notes relative to each entry, as well as full page views. Buttons to access each full page view are placed at the bottom of the folder sidebar by default when installed for easy quick one click access between emails, scheduled events/calendar, and your To-Do list. All this and more right in your email client where it's most handy. Completely customizable to your liking. You can toggle the Lightening sidebar on or off just as you can the folder/account sidebar.

You also have three built-in window views of your choice to define how you prefer your Thunderbird GUI layout-(>View >Layout >(classic | wide | vertical). Incoming emails can be threaded if you choose so you can keep an ongoing conversation and all it's responses together... and so much more.

Once you customize and familiarize yourself with Thunderbird, you won't ever want to use anything else simply because nothing else compares! After you use and become familiar with Thunderbird, using any other email client will make you appreciate what it does, and can do, that no other email client can. Use Thunderbird and don't look back. As I stated above, I could go on forever about the features and benefits of Thunderbird, but have her try it and I'm sure she'll like it.

I personally couldn't live without Thunderbird and would be so frustrated using anything else after missing all the features and custom tools/add-ons. No other email client allows you to customize it to your needs like Thunderbird -- hands down. Thunderbird can go with you no matter where you go regarding OS choice, so you'll always be familiar with it and never again have to learn another email client simply because it happens to be built-in to the OS of choice.

That's my 2¢! Hope I've helped make the decision easy and persuaded you and your friend to use Thunderbird. You won't regret it IMO. ;)


[B]Regards,
Visible Spirit[/B]

---

### Post by lorenzosu on 2009-11-23
I am currently using Thunderbird because of its incredible portability which allows me to be very mobile in fact:
- It's cross-platform. This way I can have a copy of my profile on an usb drive move seamlessly from my work computer (Windows) to my home one (Ubuntu) to my work laptop when I travel etc. (and I also keep a portable version for Windows for internet café or similar).
- Because everything is based on profiles (much like Firefox) everything is preserved when you move to another machine: folder structure, filters, spam rules, views, read/unread status etc.
- I can easily back-up everything (including extensions, settings, accounts etc) by simply copying (and optionally gzipping) the whole profile folder, possibly making different snapshots.
- One last neat feature, which is actually an extension, is the ability to change SMTP on the fly with a button: again very very handy for portability (an of course extensions are another powerful point).

Just a last note: If like me you are using POP email one crucial setting for 'disaster recovery' is to instruct Thunderbird not to delete messages from the server immediately, but keep them for at least 2 days (especially now that most ISP have raised their quota on servers, I have it set to 10 days and never had server-full errors)

That said I would be willing to have the wonderful Exchange integration and of course GNOME one as well which Evolution has in Thunderbird as well

Kind regards,
Lorenzo.

---

### Post by garikaib on 2009-11-23
Evolution is great but I prefer Thunderbird since I use it on windows too. The transition appears seamless.

---

### Post by z0mbie on 2009-11-23
The UI in Thunderbird 3.0 is excellent! Evolution's UI is so grossly cluttered. Thunderbird has great support for Gmail Contact and Google Calendar sync. I use Thunderbird on Windows/Mac/Linux.

---

### Post by underquark on 2009-11-23
She can use both.  Then she'll end up using the one she likes best.  I use Evolution because it was installed automatically and because I like its calendar.

The only use I had for Thunderbird was under Windows when moving mail from Outlook (import Outlook .pst files into Thunderbird, copy the .mbox files over to Evolution machine).  Lately I have used "pstread" to convert them.

---

### Post by trixman on 2009-11-25
> **underquark said:**
> She can use both.  Then she'll end up using the one she likes best.  I use Evolution because it was installed automatically and because I like its calendar.

The only use I had for Thunderbird was under Windows when moving mail from Outlook (import Outlook .pst files into Thunderbird, copy the .mbox files over to Evolution machine).  Lately I have used "pstread" to convert them.

thanks to all for the great posts

right now she is using evolution and she really enjoys it. the calender feature she loves & contacts.

---

### Post by leveliv on 2009-11-25
thunderbird has a calendar function as well. I am currently using Beta 4 its awesome. It configures Gmail automatically no more entering server numbers etc. it's very convenient. but I also tried to used Evolution but I could never get used to it.

---

### Post by s9032g@comcast.net on 2009-12-02
If you go with Thunderbird don't try to delete Evolution as it will mess you up. Ubuntu is not so free will as it seems,

---

### Post by RJ12 on 2009-12-02
Well I have decided to try Thunderbird and would recommend it for people who just need a simple email client (I have no problem with no calendar as I use my Palm m130(I know its old but gets the job done) and I havent tried any themes so off to try those) but those who want to have calendering and tasking integrated as preinstalled then choose Evolution:p plus just because its not preinstalled its still easy to install

sudo apt-get install thunderbird
(I know there is a download that you can compile...)

---

### Post by pauwl on 2009-12-09
We found that when moving larger numbers of people over from Microsoft Outlook or Outlook express, users had fewer issues with evolution - probably because of the similarity of interfaces.

I'm not too impressed with either one's off-line working though. Maybe my mailbox is too large.

---

### Post by poliltimmy on 2009-12-09
I refuse to use a program that can not be removed, without causing problems ie. evolution. Not to mention the sorry excuse for a sound server called  pulse audio. I switched to Linux, just find it isn't as free to alter as stated.

---

### Post by natrium42 on 2009-12-11
I switched back to Thunderbird after my messages history got corrupted by Evolution. Messages appeared multiple times and wouldn't stay deleted... Thunderbird 2 was very slow to search IMAP folders, but Thunderbird 3 has much better IMAP handling. Maybe Evolution is better in some regards, but at least I know that Thunderbird will not eat my messages...

---

### Post by Georgia boy on 2010-01-06
I had removed Evolution but reinstalled this morning after reading how it can mess with ubuntu. I tried to use it but, keep can only send out not receive. When I try to receive it asks for the log in then gives me an error about user/password not found or something like that. Sorry, not at home computer. Going back to Thunderbird. Used that in Windows and using it for here also. Setup my own backgrounds in it and like the way it works. For some reason I have never gotten Evolution to work. That's why I had deleted it in the first place.
Hope that it's removed from being default in the 10.04 that's due in April. 

Tom
Hi. Got Evolution to receive emails. Stupid mistake on my part of putting email address in user field. After correcting that Evolution worked. But, still prefer Thunderbird over Evolution. I use the Lightning addon for the calender and don't really need anything else yet. To me Thunderbird is cleaner and easier to use.

Tom

---

### Post by kgarbutt on 2010-01-06
I use thunderbird because I like just an email client without all the extras.

---

### Post by Mukoi on 2010-09-04
How do you import emails and address book from Evolution to Thunderbird?

---

### Post by richwein on 2010-10-01
I hope this is not a dumb question.

I think Thunderbird and Evolution can use mbox email files.

Is it possible to configure both Thunderbird and Evolution to use the same mbox file ?  

If that were possible, then Thunderbird or Evolution simply become a user interface for your emails in the mbox file.  You could use Thunderbird on Monday and Evolution on Tuesday.

---

