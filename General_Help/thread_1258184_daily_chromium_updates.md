---
title: "daily chromium updates"
date: 2009-09-04
forum: General Help
---

### Post by 16sinker on 2009-09-04
I downloaded chromium browser about a week ago, to try it out and see how it compares to firefox browser. It is installed and I am trying to get used to it. At this point, imo, it doesn't come close to firefox. I realize chromium is still in development and is incomplete so I am going to keep it and see how it evolves. My question is: Why am I getting the same updates every day? My update manager indicates the updates are-chromium browser(11.0mb) and chromium-codecs-ffmpeg(369kb). In the lower portion of the update manager page, under the changes tab, it says "failed to detect distribution." Today I got these updates twice. The updates apparently load and I run sudo apt-get autoremove, sudo apt-get autoclean and sudo localepurge to remove the files that have been replaced by the latest update. After each update I check chromium to see if there are any changes in functionality-there aren't. So what's going on? Are these updates daily builds? I'm getting no indication that there are errors, other than the "failed to detect distribution" and the updates load like any other update.

---

### Post by fragos on 2009-09-04
The updates are daily builds. Most of the time you won't detect what the changes are. You can start chromium with "--enable-plugins" which will get flash to work for many sites like youtube.

---

### Post by 16sinker on 2009-09-04
Thank you very much-I'll continue to take my updates and hope chromium will soon equal firefox.

---

### Post by darco on 2009-09-04
> **16sinker said:**
> Thank you very much-I'll continue to take my updates and hope chromium will soon equal firefox.

Wow, I am the opposite...apart from the extensions, Chromium to me exceeds FF. It even has adsweep which is really all I need. I dont use noscript it Linux, only in my Win box.
Java and x64 Flash work flawlessly. I have a feeling you dont have your repository setup properly to d/l the daily builds. I have never seen duplicate updates ever.
Ill hunt down the proper repo and post back

darco

*edit" ok, here is the repo for chromium
sudo add-apt-repository ppa:chromium-daily

[http://www.adsweep.org/](http://www.adsweep.org/)

---

### Post by 16sinker on 2009-09-04
Adsweep is exactly what I need for chromium. How do I get it Darco?

---

### Post by gradinaruvasile on 2009-09-04
Run the attached script. It will install Chromium for u. Plugins+adblocker enabled. Enjoy!

---

### Post by 16sinker on 2009-09-04
> **darco said:**
> Wow, I am the opposite...apart from the extensions, Chromium to me exceeds FF. It even has adsweep which is really all I need. I dont use noscript it Linux, only in my Win box.
Java and x64 Flash work flawlessly. I have a feeling you dont have your repository setup properly to d/l the daily builds. I have never seen duplicate updates ever.
Ill hunt down the proper repo and post back

darco

*edit" ok, here is the repo for chromium
sudo add-apt-repository ppa:chromium-daily

[http://www.adsweep.org/](http://www.adsweep.org/)
I tried command "sudo add-apt-repository ppa:chromium-daily and got no such command and I tried "sudo apt-get add-apt-repository ppa:chromium-daily and got the same return. Proper command please.

---

### Post by 16sinker on 2009-09-04
> **gradinaruvasile said:**
> Run the attached script. It will install Chromium for u. Plugins+adblocker enabled. Enjoy!

I've downloaded the script, it resides on my desktop as Chromiumlnstaller.sh. I open the script and click "save", but apparrently I've done something wrong, as I still have ads on the web pages in Chromium. Question. Will Adsweep only function in Chromium or will it function on Firefox as well?

---

### Post by joshuapbell on 2009-09-04
> **16sinker said:**
> Thank you very much-I'll continue to take my updates and hope chromium will soon equal firefox.

It will never equal firefox, it isn't designed to equal firefox. It is an alternative, just like Linux will never equal Windows, it is simply an alternative... each with there bad and good.

---

### Post by 16sinker on 2009-09-04
> **joshuapbell said:**
> It will never equal firefox, it isn't designed to equal firefox. It is an alternative, just like Linux will never equal Windows, it is simply an alternative... each with there bad and good.

Thanks for your opinion. It's my opinion that Linux already equals and surpasses Windoze.

---

### Post by darco on 2009-09-04
> **16sinker said:**
> I tried command "sudo add-apt-repository ppa:chromium-daily and got no such command and I tried "sudo apt-get add-apt-repository ppa:chromium-daily and got the same return. Proper command please.

try this then:

sudo su
echo "deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main #chromium-browser" > /etc/apt/sources.list.d/chromium.list
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xfbef0d696de1c72ba5a835fe5a9bf3bb4e5e17b5
sudo apt-get update && sudo apt-get install chromium-browser

---

### Post by 16sinker on 2009-09-04
> **darco said:**
> try this then:

sudo su
echo "deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main #chromium-browser" > /etc/apt/sources.list.d/chromium.list
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xfbef0d696de1c72ba5a835fe5a9bf3bb4e5e17b5
sudo apt-get update && sudo apt-get install chromium-browser
My output:
bofus@ubuntudell:~$ sudo su
[sudo] password for bofus: 
root@ubuntudell:/home/bofus# echo "deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main #chromium-browser" > /etc/apt/sources.list.d/chromium.list
root@ubuntudell:/home/bofus# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xfbef0d696de1c72ba5a835fe5a9bf3bb4e5e17b5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 0xfbef0d696de1c72ba5a835fe5a9bf3bb4e5e17b5
gpg: requesting key 4E5E17B5 from hkp server keyserver.ubuntu.com
gpg: key 4E5E17B5: "Launchpad PPA for chromium-daily" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
root@ubuntudell:/home/bofus# sudo apt-get update && sudo apt-get install chromium-browser
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US       
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.7kB]               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release.gpg            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security Release.gpg              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/restricted Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/main Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/universe Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Sources                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Sources
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages [3240B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Sources
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources [1520B]          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/universe Packages
Fetched 79.7kB in 1s (40.3kB/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages (/var/lib/apt/lists/ppa.launchpad.net_chromium-daily_ppa_ubuntu_dists_jaunty_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages (/var/lib/apt/lists/ppa.launchpad.net_chromium-daily_ppa_ubuntu_dists_jaunty_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty-backports_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
chromium-browser is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntudell:/home/bofus#

---

### Post by darco on 2009-09-04
What version of Chromium are you running?

darco

---

### Post by 16sinker on 2009-09-04
That would be Chromium 4.0.207.0(ubuntu build 25449) under "about Chromium."

---

### Post by darco on 2009-09-04
well thats the latest build. So now that we know you have the right repos, I dont know why you are getting those "failed" errors.  What other issues are you having?  

darco

---

### Post by 16sinker on 2009-09-04
Actually, Update Manager indicates "Failed to detect distribution" but proceeds to load the update. I don't think I have any issues, as I'm using Chromium now and everything seems to be in order. So other than the "duplicate sources.list entries" when I apt-get update and being unfamiliar with Chromium, but learning, I don" perceive any issues.

---

### Post by darco on 2009-09-04
The duplicate error means that you have the repo in both the source.list and in the sources.list.d folder. Delete it from the source.list and that error will disappear.
I use Chromium as my default browser and I think its a great broweer.

darco

---

### Post by 16sinker on 2009-09-04
I'm on a steep learning curve with Chromium and am discovering details about the browser the more I use it, and have found it to be very fast-faster than FF, and will probably make it my default, when I am comfortable using it. Now as to the duplicate sources.list entries-Do I delete them completely from sources.list, or just one of the duplicates?

---

### Post by darco on 2009-09-04
Just from the source.list....do you have the other folder I mentioned?
Funny how your first post you were negative about Chromium and now...heh

darco

---

### Post by 16sinker on 2009-09-04
Sorry, didn't mean to come across as negative, relative Chromium compared to Firefox. The few times that I have used Chromium, I realized that it was much faster than FF, but I wasn't familiar with using it. Tonight I am using it and discovering new details by the minute. So thanks for your help today and in the past.

---

### Post by garvinrick4 on 2009-09-04
Just open Chromium next to Firefox?

See which one renders Jpeg's, fonts even gif better.

Chromium is far superior if that is what you are looking for.

Firefox has far more bells and whistles.

I think it is one of those what ever floats your boat type questions.

Beauty is in the eye of the beholder.

That is my drift on it anyway. 

I have always been attracted to beauty and simplicity and they never in my
world have gone hand in hand. Beauty always came with a price.

Chromium simple and beautiful and the price is right, I take her over Firefox.

---

### Post by 16sinker on 2009-09-04
I've been using FF for five years now and the price for him is right imho. I've used Chromium for one week and I have to admit that Chromium is faster, but at this point I'm more comfortable using FF and as I've posted previously, I will switch when I become more proficient using Chromium. So thanks for your input-I won't disagree with anything in your last post.

---

### Post by themusicalduck on 2009-09-04
> **garvinrick4 said:**
> 
See which one renders Jpeg's, fonts even gif better.


The fonts on Chromium look terrible for me compared to Firefox (3.5). All squashed up, ugly and unclear. Maybe I'm missing a setting somewhere that improves them?

---

### Post by 16sinker on 2009-09-04
> **darco said:**
> Just from the source.list....do you have the other folder I mentioned?
Funny how your first post you were negative about Chromium and now...heh

darco
Since I didn't respond to your query about sources.list.d; yes,I do have that folder. Also, since we have addressed Adsweep in this thread, I would appreciate some help installing the script. I have it on my desktop as Adsweep.user.js and can't figure out how to use it. Thanks.

---

### Post by 16sinker on 2009-09-04
Help from anyone, relative installing Adsweep in Chromium, would be appreciated. [COLOR="Black"][SIZE="4"][FONT="Arial Black"][/FONT][/SIZE][/COLOR]

---

### Post by darco on 2009-09-04
yo...just download the .crx and chromium should pick it up and install....just like th Themes....

darco

---

### Post by 16sinker on 2009-09-05
Thanks Darco. Didn't know to load the.crx. Worked like a charm. No ads!!! Now I need to know how to make Chromium/default, since I've deleted the pop-up,"Chromium is not your default browser" notification. Funny how preferences change over a short period if time.

---

### Post by garvinrick4 on 2009-09-05
Everything I look at in Chromium in fonts looks fantastic.
What type of fonts do you have. Microsoft Core fonts  TrueType.
      Gnome

Desktop System,Appearance,fonts tab

Use Times Roman Bold 13
 Dito                12
 Dito                12
 Dito                12
Courier New Bold     11

Sub pixel smooth  if LCD

If it doe's not let Chromium and your Desktop look good. Let me know.

IN Chromium Encoding  Western ISO

This just works for me, eye of beholder. 
But they should not look like you said not Clear Type and scrunched up.

This is kind of remedial you must likely have nice fonts installed
but something is terrible wrong. Chromium gets rave revues on their appearance and rendering engine and it shows. Give it a Google.

---

### Post by darco on 2009-09-05
> **16sinker said:**
> Thanks Darco. Didn't know to load the.crx. Worked like a charm. No ads!!! Now I need to know how to make Chromium/default, since I've deleted the pop-up,"Chromium is not your default browser" notification. Funny how preferences change over a short period if time.

Wrench/Options/Basic....

Fonts;;Liberation Sans!!!

darco

---

### Post by 16sinker on 2009-09-05
> **darco said:**
> Wrench/Options/Basic....

Fonts;;Liberation Sans!!!

darco
Simple enough. Thanks.

---

### Post by themusicalduck on 2009-09-05
> **garvinrick4 said:**
> Everything I look at in Chromium in fonts looks fantastic.
What type of fonts do you have. Microsoft Core fonts  TrueType.
      Gnome

Desktop System,Appearance,fonts tab

Use Times Roman Bold 13
 Dito                12
 Dito                12
 Dito                12
Courier New Bold     11

Sub pixel smooth  if LCD

If it doe's not let Chromium and your Desktop look good. Let me know.

IN Chromium Encoding  Western ISO

This just works for me, eye of beholder. 
But they should not look like you said not Clear Type and scrunched up.

This is kind of remedial you must likely have nice fonts installed
but something is terrible wrong. Chromium gets rave revues on their appearance and rendering engine and it shows. Give it a Google.

Using those settings didn't appear to even make any change to chromium. So you could be right, something might not quite be working :S

I do have microsoft fonts enabled and Cleartype enabled. I even tried deleting the chromium config folder but still doesn't look as good as firefox.

---

### Post by darco on 2009-09-05
I changed my fonts within chromium and not for the whole system like posted above....

darco

---

### Post by themusicalduck on 2009-09-05
> **darco said:**
> I changed my fonts within chromium and not for the whole system like posted above....

darco

Ah yes.. Found it, thanks!

---

### Post by 16sinker on 2009-09-06
I,ve been looking for the last two days and nowhere in Chromium under the "wrench" do I find desktop system>appearance>fonts tab. Can you help me?

---

### Post by fragos on 2009-09-07
wrench-> Options-> Under the Hood-> Scroll down to "Change font and Language settings" button.

---

### Post by dBuster on 2009-09-07
Okay, Chromium is slick indeed.  however I am having issues with the website pogo.com in getting the java games to run.  They run fine in my Shiretoko Firefox 3.5 so why not with chromium?  Anyone else get them to run or not?

---

### Post by 16sinker on 2009-09-08
OK, I found the fonts tab, but....when I choose a font other than default, I'm not seeing any difference on web pages. The fonts remain small, nothing like the example on the option window when I choose one. Also, when I choose a bold font and it's displayed in the example, it doesn't show up as the choice I made. I've got to be doing something wrong.

---

### Post by fragos on 2009-09-08
Try setting font size to 16, worked for me.

---

### Post by 16sinker on 2009-09-08
I've set font size to 30 and it has no result, even though in the example in the "pick a font" window reflects the point size 30. Again, the larger font size is not reflected when a webpage is rendered.

---

### Post by darco on 2009-09-08
> **16sinker said:**
> I've set font size to 30 and it has no result, even though in the example in the "pick a font" window reflects the point size 30. Again, the larger font size is not reflected when a webpage is rendered.

Maybe you need to "match" the fonts under Appearance to the same as what you have in Chromium?
Mine do and I can change font size w/o a prob.

darco

---

### Post by darco on 2009-09-08
> **dBuster said:**
> Okay, Chromium is slick indeed.  however I am having issues with the website pogo.com in getting the java games to run.  They run fine in my Shiretoko Firefox 3.5 so why not with chromium?  Anyone else get them to run or not?

That java site does not work for me either.....

darco

---

### Post by darco on 2009-09-13
Whats going on w/Chromium? I havent received a new build since the 8th? I noticed on the PPA webpage another failed build (26091). This has been going  probably since the 8th...dang, the devs must be pulling their hair out!

darco

---

### Post by mhenriday on 2009-09-15
If memory doesn't fail, the last update I received - **4.0.207.0 (Ubuntu build 25615)** - was released on 4 September. Anybody know what's going on with the ppa ? From what I've seen on other fora, the latest **Chromium** release for Linux seems to be **4.0.210.0 (26206)**, which I've now installed manually. But the ppa is far more convenient - any suggestions as to how we can get it working again ?...

Henri

---

### Post by prasathpr on 2009-09-15
Thanks for our information it's very usefull............

---

### Post by dBuster on 2009-09-15
What ever happened, my chromium also was not updating automatically with the daily builds until this morning!  I received an update!  Wahoo!!

---

### Post by rsmereka on 2009-09-15
> **gradinaruvasile said:**
> Run the attached script. It will install Chromium for u. Plugins+adblocker enabled. Enjoy!
I am not a fan of Google's Chrome. It's stable enough and certainly fast enough and small enough but the [big brother stuff]("http://blog.broadcastengineering.com/brad/2009/07/27/is-google-becoming-big-brother/")
scares me. As an alternative, I have been using [Iron]("http://www.srware.net/en/software_srware_iron.php") which is Chrome without the scary stuff.

To get Adsweep working as a user script under Iron, I took gradinaruvasile's shell script and stripped out the download of Chrome. This modified version only contains the creation of the user directories and downloading Adsweep as a user script.

I managed to get Adsweep as a user script working for Iron under Lunix (Ubuntu 9.04). Here's how:

All you have to do is to make sure that you execute Iron with the
```
--enable-user-scripts
``` option.

Just copy, paste, save as a file and make the file executable.

```
#!/bin/bash
mkdir -p ~/.config/chromium/
mkdir -p ~/.config/chromium/Default/
mkdir -p ~/.config/chromium/Default/User\ Scripts
wget -qO ~/.config/chromium/Default/User\ Scripts/AdSweep.user.js http://www.adsweep.org/AdSweep.user.js

# don't forget to execute with the option --enable-user-scripts
```
One more task you need to be concerned about. Updates to the Adsweep file. Create a shell script from this:
```
cd ~/.config/chromium/Default/User\ Scripts
wget -N -P . http://www.adsweep.org/AdSweep.user.js
```
Then run the shell script in a cron job to update once a day.

Enjoy,
Rick

---

### Post by mhenriday on 2009-09-15
Thanks for the tip, **dBaser**, «Wahoo» is indeed *le mot juste* ! After reading your posting above, I went directly to my update manager and indeed, there was a **Chromium** update waiting for me. Now I can uninstall the manually installed version, in the fond hope that **Launchpad** won't go bonkers in the next couple of days....

**Rick**, I've been thinking of installing **Iron**, just to see how it works, but have hitherto been too lazy. Does one have to install a new build every day, or can one get it to update automatically like **Chromium** (when the ppa works, that is) ?...

Henri

---

### Post by rsmereka on 2009-09-15
> **mhenriday said:**
> 
**Rick**, I've been thinking of installing **Iron**, just to see how it works, but have hitherto been too lazy. Does one have to install a new build every day, or can one get it to update automatically like **Chromium** (when the ppa works, that is) ?...

Henri
Hi Henri,
Iron Updates are from the gzip (already compiled) on the SRWare site and unfortunately, there is no automatic thingy. As a matter of fact, Iron for Linux is classified as alpha and is only available on their forum [here]("http://www.srware.net/forum/viewtopic.php?f=18&t=561")

I use Iron day-to-day on Linux and Windoze. If there was a BSD and Mac version, I would also use it there. I have no issues with it whatsoever. No crashes. everything just works. Finding out that adblock.ini is not supported for Linux was kind of silly but now that I have Adsweep installed, I think I like it better.

Rick

---

### Post by VastOne on 2009-09-15
> **darco said:**
> try this then:

sudo su
echo "deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main #chromium-browser" > /etc/apt/sources.list.d/chromium.list
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xfbef0d696de1c72ba5a835fe5a9bf3bb4e5e17b5
sudo apt-get update && sudo apt-get install chromium-browser

This one work flawlessly for me...

Thanks!

---

### Post by VastOne on 2009-09-15
> **garvinrick4 said:**
> Just open Chromium next to Firefox?

See which one renders Jpeg's, fonts even gif better.

Chromium is far superior if that is what you are looking for.

Firefox has far more bells and whistles.

I think it is one of those what ever floats your boat type questions.

Beauty is in the eye of the beholder.

That is my drift on it anyway. 

I have always been attracted to beauty and simplicity and they never in my
world have gone hand in hand. Beauty always came with a price.

Chromium simple and beautiful and the price is right, I take her over Firefox.

Well said.  I just caught the Chromium threads today and decided to give it a whirl. Like you,simple and elegance is good for me. The speed is there and mayhap FF 4 or 3.6 whichever it will be, will be better than this. At that time, I will reevaluate. I think FF has become a bit heavy and it is nice to just load my default pages and let me get my work done.

---

### Post by VastOne on 2009-09-15
Any one found out to have Chromium start back with the same font sizes that you started with if you have changed the sizes with ctrl +?

I have to resize it each time I open it.

---

### Post by JigglyWiggly_ on 2009-09-15
Chrome/Chromeium are the better alternatives to firefox, mainly becuase it's insanely faster. It isn't as stable though for sure, but I just have a fetish for webkit browsers. :)

---

### Post by fragos on 2009-09-15
> **VastOne said:**
> Any one found out to have Chromium start back with the same font sizes that you started with if you have changed the sizes with ctrl +?

I have to resize it each time I open it.

For permanent font size settings I think you have to use Options under the wrench.

---

### Post by mhenriday on 2009-09-16
**Rick**, thanks for the link ! The version name - **3.0.197 Alpha** - makes me suspect that the new **Iron**, which was released about a month ago, is based upon the **Chrome** beta version for **Windows**, i e, version 3. From my experience with earlier versions of **Chromium**, **SCIM** won't work with it, so I'll postpone trying **Iron** until a version based on **Chrome 4** is released. But I've bookmarked the **SRWare** site (by the way the site admin's photo makes me wonder if he isn't working for the Bundesnachrichtendienst)....

Henri

---

### Post by opensourcederry on 2009-09-16
My latest version of Chromium from daily builds repo is 4.0.209.0 (Ubuntu Build 26159) and it now enables flash by default.

Works a treat and lightening fast, almost as good as moving up a notch with isp.

---

### Post by rifak on 2009-09-16
i havent been getting any chromium updates for about a week now...can anyone else confirm this? im at version 4.0.207.0 (Ubuntu build 25615) in hardy. and yes, i have been getting them since the beginning (ive been using chromium for a couple months now with regular updates) and they just seemed to stop. can anyone else confirm this in hardy?

---

### Post by screaminj3sus on 2009-09-17
I prefer firefox over chrome in windows, but firefox is such a slow POS in linux, chrome feels much faster. And its coming along quite nicely in linux.

---

### Post by rifak on 2009-09-17
welp, maybe i spoke too soon...an update just came. i am now at 4.0.212.0 (Ubuntu build 26339) in hardy.

---

### Post by dBuster on 2009-11-04
Anyone else crashing when trying to type in a web address or search term into the address line?

I can no longer type in a website address!  I crash hard meaning I have to power down to get the pc back up.  Thought maybe an update would fix but it hasn't.  At a loss on where to begin troubleshooting this.

---

### Post by fragos on 2009-11-04
I'm running 9.10 and get daily Chromium updates. Currently at 4.0.233.0 (Ubuntu build 30813). I'm not having the problem you are. The only trouble I'm seeing are with some interactive pages which I assume are using Javascript which come up but don't render.

---

### Post by mhenriday on 2009-11-05
> **dBuster said:**
> Anyone else crashing when trying to type in a web address or search term into the address line?

I can no longer type in a website address!  I crash hard meaning I have to power down to get the pc back up.  Thought maybe an update would fix but it hasn't.  At a loss on where to begin troubleshooting this.

**Dbuster**, you seem to indicate that the problem you describe with **Chromium** has arisen recently ; i e, that previously you were able to type addresses in the address bar. Is this interpretation correct ? If so, can you recall with which **Chromium** update the problem started ? I've never seen this on my AMD 64-bit setup, neither with **Jaunty** previously nor with **Karmic**, which I've been running since the beta version became available. I'm presently running **Chromium 4.0.236.0 (Ubuntu build 31004)** with no problems, aside from the fact that bookmarks sync is still not available for **Linux**....

Henri

---

### Post by jolidon me on 2009-12-07
due to some [bug]("http://code.google.com/p/chromium/issues/detail?id=9171") Chromium requires the *msttcorefonts* package to actually show content (otherwise it will just show a blank content area). So, make sure to have multiverse repositories enabled and also type:

---

### Post by Thelasko on 2009-12-07
Does anybody know how to report bugs for Chromium?  Saturday's update seems to have created some rendering issues.  When I scroll down a page some of the page occasionally turns black.  I have to scroll back and forth to get it to render properly again.

---

### Post by mhenriday on 2009-12-07
**Thelasko**, here's the [COLOR="Blue"]_**[link]("http://www.chromium.org/for-testers/bug-reporting-guidelines")**_[/COLOR] you need....

Henri

---

### Post by Claritux on 2009-12-07
I've got the same bug. Does anyone know if it's possible to roll back to a pre-weekend build meanwhile?

---

### Post by fragos on 2009-12-07
I have the rendering problem as well -- it does seem to relate cursor movement. With daily releases I'll just wait for fix. It can't be far away since it's hard to miss this problem. I also use Epiphany as a backup. I'm a web site designer and wish I could make Chromium use Gedit to view source code like Epiphany does.

---

### Post by darco on 2009-12-07
wow, ver 33962 is even worse!...hopefully they will square it away soon


darco

---

### Post by l-x-l on 2009-12-07
> **Thelasko said:**
> Does anybody know how to report bugs for Chromium?  Saturday's update seems to have created some rendering issues.  When I scroll down a page some of the page occasionally turns black.  I have to scroll back and forth to get it to render properly again.

Same problem. Chromium is almost unusable now. Going back to FF.

---

### Post by l-x-l on 2009-12-08
> **Thelasko said:**
> Does anybody know how to report bugs for Chromium?  Saturday's update seems to have created some rendering issues.  When I scroll down a page some of the page occasionally turns black.  I have to scroll back and forth to get it to render properly again.

> **l-x-l said:**
> Same problem. Chromium is almost unusable now. Going back to FF.

Problem seems to be fixed now with the latest updates. Sweet.

---

