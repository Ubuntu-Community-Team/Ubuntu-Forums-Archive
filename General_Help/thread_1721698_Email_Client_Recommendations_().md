---
title: "Email Client Recommendations (?)"
date: 2011-04-04
forum: General Help
---

### Post by Weighty Ghost on 2011-04-04
Hey Everyone,

I searched a couple of pages deep, but couldn't find the exact info I was looking for.

Currently, I'm using T-bird for email on my Windows partition, but it doesn't look like there is an export function.

I have to set up my business email accounts on Ubuntu, and was just wondering whether it was easier to migrate to Evolution or could I simplify the process by sticking w/ Thunderbird for Ubuntu (?)

Anyone, been through this lately? What tutorials did you find most helpful?

To be honest, I would'nt mind just setting things up manually, but  embarrisinly I can't recall a single one of my passwords....,

---

### Post by crossedout on 2011-04-04
Hi Ghost,

I remember a while back I used to share the TB info between partitions, where whatever I did in Windows or Ubuntu showed up in the other.  I had to use a FAT partition between them but it served its purpose nicely.

Ultimately, I wound up doing what you already stated which is use Evolution for biz purposes.  Several reasons why, but mostly because Windows is just a tool that I keep around now and don't need to share the email via TB.

If you decide to start from scratch and don't need to share the information between OS's then I'd still go with TB.  I would have already myself except that I have no immediate need to.

-Xout

---

### Post by seawolf167 on 2011-04-05
The easiest would probably be to stick with Thunderbird on Ubuntu. The community documentation is located [here]("https://help.ubuntu.com/community/Thunderbird").

In case you want to switch to Evolution, you can migrate your Thunderbird data to Evolution. A how-to is located [here]("http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Howto_migrate_from_Thunderbird_to_Evolution"). It's a little old, but most everything is the same - I know there are a couple different wordings in the new version, but everything still works.

---

### Post by Weighty Ghost on 2011-04-24
[LEFT]Thanks for the input guys,

For anyone doing a search here is the short version...

In Windows Vista
1. Open T-Bird and un-install  all Windows specific extensions.
2. Copy contents of,  C:\Users\<Windows user name>\AppData\Roaming\Thunderbird\Profiles\<Profile name>\ 

In Ubuntu
1. Install Thunderbird via Software Center
2. Run it and put a bunch of dummy info in when prompted to setup your new profile
3. Go to Home directory  ant hit CTRL+H to diplay hidden folders.
4. Go to <.thunderbird> folder, and open the <Profilename> folder.
5. Paste the contents of your Windows profile, overwriting the Ubuntu folder contents
[/LEFT]

---

