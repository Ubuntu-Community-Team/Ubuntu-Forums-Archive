---
title: "Installing Office 2010 on Ubuntu 11.04"
date: 2012-02-09
forum: General Help
---

### Post by BenettFreeman on 2012-02-09
I've followed many different How To guides in order to install Office 2010 on Ubuntu, but none of them have worked for me, and I get the error message:-

"Installation language not supported"

Can anyone help me get this installed once and for all please?

---

### Post by winh8r on 2012-02-09
I do not mean to cause any offence, but why would you need to install Office on Ubuntu?

Open Office or Libre Office do everything that Office 2010 does and they can save the documents in any format compatible with Office.

The layout is not that much different either.

Just wondered if you are giving yourself unnecessary headaches?


Please do not take this the wrong way, I am merely curious.

---

### Post by BenettFreeman on 2012-02-09
Don't get me wrong, I loathe the Microsoft Corporation, but I'm afraid I cannot agree with the statement that Open Office and Libre Office do everything that MS Office does.

First of all, those suites do not properly handle MS formats, and there are all kinds of formatting problems that stem from opening DOCX in them, or opening files authored in Open Office in MS apps etc.

Second of all, the editing and review functionality is nowhere near as developed.

As an editor, I need to have MS Office 2010, and while up until recently I was dual-booting, that is no longer an option since a very nasty Trojan took out my last Win 7 installation and I really can't be bothered with the hassle of trying to maintain a Windows OS anymore.

Therefore, the only solution to my problem is to get MS Office 2010 working under Wine or Crossover. The plethora of walkthroughs on the subject have all sadly failed, hence my asking for help on here.

[EDIT: I love your sig btw. Am a huge fan of FZ]

---

### Post by drmrgd on 2012-02-09
Check out this thread here:

[Installing MS Office 2010 in Wine]("http://ubuntuforums.org/showthread.php?t=1885051")

I still haven't gotten around to setting this up myself.  But, it seems a lot of people are finding this method successful.  I too find it difficult to work with Open Office and / or Libre Office for many tasks.

---

### Post by QIII on 2012-02-09
According to WineHQ reviews, the 64 bit installer is garbage, but the 32 bit version is silver.

---

### Post by cogier on 2012-02-09
This is an interesting debate. Do you run Windows software on Windows or on Linux?

I would argue that if you want to run Office you run it under Windows.

I would also add that if you have to run MS Office under Ubuntu use MS Office 2003 as that version does work.

I have just looked at the Wine web site here [http://appdb.winehq.org/appview.php?appId=31]("http://appdb.winehq.org/appview.php?appId=31") 

It might help - BUT if you want MS software use Windows not Linux.

---

### Post by winh8r on 2012-02-09
> **BenettFreeman said:**
> Don't get me wrong, I loathe the Microsoft Corporation, but I'm afraid I cannot agree with the statement that Open Office and Libre Office do everything that MS Office does.

First of all, those suites do not properly handle MS formats, and there are all kinds of formatting problems that stem from opening DOCX in them, or opening files authored in Open Office in MS apps etc.

Second of all, the editing and review functionality is nowhere near as developed.

As an editor, I need to have MS Office 2010, and while up until recently I was dual-booting, that is no longer an option since a very nasty Trojan took out my last Win 7 installation and I really can't be bothered with the hassle of trying to maintain a Windows OS anymore.

Therefore, the only solution to my problem is to get MS Office 2010 working under Wine or Crossover. The plethora of walkthroughs on the subject have all sadly failed, hence my asking for help on here.

[EDIT: I love your sig btw. Am a huge fan of FZ]


Thanks for your explanation, I can see where you are coming from now, like I said I hope it didn't come across as rude.

I think it maybe best to give the one suggested by drmrgd above a go to start with.

I had a look around and found this:

[http://https://help.ubuntu.com/community/Microsoft_Office]("http://https://help.ubuntu.com/community/Microsoft_Office")


which leads here:

[http://appdb.winehq.org/appview.php?appId=31]("http://appdb.winehq.org/appview.php?appId=31")

which would appear to suggest that the Office 2010 64 bit edition is a bit of a no-go.

If you are using the 32 bit edition then it seems ok.

I lifted this from the last link too just in case you missed it:

> I installed Office Professional Plus 2010 with 32-bit wine on 64-bit machine.

Before installation I did:
1) wiped out my entire wine directory
2) set default machine to Windows 7 via winecfg (when I installed Office 2010 as Windows XP, Excel did not recognize filenames longer than 8 chars)
3) installed .NET 2.0 with "winetricks dotnet20" (otherwise the installer got error)

I hope this is of some help to you.

On another note, I went to see Dweezil Zappa in November, performing the entire Apostrophe album, with a huge video screen behind the band on stage with Frank playing as part of the band, it was fabulous, and also meant that I could take my 18 year old son to see FZ "LIVE". Tremendous.

A truly inspirational musician, too often shunned by the mainstream because he spoke the truth and it scared them all!!!

Okay, enough of this , get on with the installation and let us know how you get along!

Good Luck

---

### Post by drmrgd on 2012-02-09
> **cogier said:**
> This is an interesting debate. Do you run Windows software on Windows or on Linux?

I would argue that if you want to run Office you run it under Windows.

I would also add that if you have to run MS Office under Ubuntu use MS Office 2003 as that version does work.

I have just looked at the Wine web site here [http://appdb.winehq.org/appview.php?appId=31]("http://appdb.winehq.org/appview.php?appId=31") 

It might help - BUT if you want MS software use Windows not Linux.

Yeah, I **hate** that I have to still be tethered to a few Windows things.  But, Excel is definitely one of them.  When the folks at Open / Libre Office can get their Excel clone working as well as Microsoft's, that will be a joyful day for me.  For now, though, it just doesn't cut it, and killing my Kubuntu session and booting into Windows is a pain (and don't even get me started on virtualizing with this computer...arg!).  

But, like these guys said, 2003 according to the WineHQ is better.  But, the thread that I posted a link to does have an option to try 2010 to see how it works.  Worth a quick try to me.

---

### Post by QIII on 2012-02-09
> **cogier said:**
> This is an interesting debate. Do you run Windows software on Windows or on Linux?

I would argue that if you want to run Office you run it under Windows.

I would also add that if you have to run MS Office under Ubuntu use MS Office 2003 as that version does work.

I have just looked at the Wine web site here [http://appdb.winehq.org/appview.php?appId=31]("http://appdb.winehq.org/appview.php?appId=31") 

It might help - BUT if you want MS software use Windows not Linux.

One should not presume to know best what another's needs, intentions or desires are.  In a free world one should be allowed to do things as best serves their intentions.

Wine exists for just that.  It's not something I would use, but I'm not the original poster.

Our opinions are certainly valid, but should be expressed as such.  "In my opinion..."

---

### Post by Cheesemill on 2012-02-09
I've always found it a lot easier to run Office 2010 using VirtualBox.

---

### Post by winh8r on 2012-02-09
> **Cheesemill said:**
> I've always found it a lot easier to run Office 2010 using VirtualBox.
 now THAT is a good idea!

One which had never crossed my mind.

Am I allowed to make an excuse?

I have never wanted to run it.

Am I forgiven?

---

### Post by BenettFreeman on 2012-02-10
OK well I can confirm that the HOW TO kindly supplied by drmrgd DOES WORK for those wanting to install Office 2010 (32 bit) on Ubuntu 11.04 !!!

Thank you SO much for your assistance! Someone should make that thread a sticky or something.

As far as the other points made in the interim, I just feel that Wine will not be considered a success until it allows you to easily install simple apps like Office onto a Linux machine. Having to use virtualisation is too much really, and there are display issues associated with that - not all configurations will allow a Seamless mode which properly displays all fonts etc..

This HOW TO was not TOO bad, but is still beyond most newcomers I would have thought.

As for Open Office and Libre Office, they aren't bad, but until the MS suites die a painful death they need to be imitations, not replacements.

I'm all for using Open Source file formats, but the abandonment of DOCX etc has to be a concerted effort otherwise its simply not economically viable for people who work with documents for a living.

Thank you all so much for your contributions, and winh8r, glad you got to see a great concert! :)

[IMG]http://imageshack.us/photo/my-images/685/officen.png[/IMG]PS> [Here is the proof]("http://imageshack.us/photo/my-images/685/officen.png").

[IMG]http://imageshack.us/photo/my-images/685/officen.png/[/IMG]

---

### Post by winh8r on 2012-02-10
Glad to see it worked out for you. 

Enjoy it now that you have it!!!

---

### Post by drmrgd on 2012-02-10
> **BenettFreeman said:**
> OK well I can confirm that the HOW TO kindly supplied by drmrgd DOES WORK for those wanting to install Office 2010 (32 bit) on Ubuntu 11.04 !!!

Thank you SO much for your assistance! Someone should make that thread a sticky or something.

As far as the other points made in the interim, I just feel that Wine will not be considered a success until it allows you to easily install simple apps like Office onto a Linux machine. Having to use virtualisation is too much really, and there are display issues associated with that - not all configurations will allow a Seamless mode which properly displays all fonts etc..

This HOW TO was not TOO bad, but is still beyond most newcomers I would have thought.

As for Open Office and Libre Office, they aren't bad, but until the MS suites die a painful death they need to be imitations, not replacements.

I'm all for using Open Source file formats, but the abandonment of DOCX etc has to be a concerted effort otherwise its simply not economically viable for people who work with documents for a living.

Thank you all so much for your contributions, and winh8r, glad you got to see a great concert! :)

[IMG]http://imageshack.us/photo/my-images/685/officen.png[/IMG]PS> [Here is the proof]("http://imageshack.us/photo/my-images/685/officen.png").

[IMG]http://imageshack.us/photo/my-images/685/officen.png/[/IMG]

Very cool!  Glad that worked.  Maybe I'll stop being lazy and try to set it up myself this weekend.  :p

---

