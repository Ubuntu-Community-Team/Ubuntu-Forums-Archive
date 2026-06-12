---
title: "convert your computer into a telephone"
date: 2012-05-23
forum: General Help
---

### Post by dmobley88 on 2012-05-23
for those of you that need a telephone, and can't afford the service, this guide is for you.

I spent hours looking for this information and went through hundreds of sites before I figured this out. I don't want to see anyone else go through that.

Requirements:

-A working internet connection
-Enough space on your HDD to install Ubuntu


What you need to do:

1) go to iptel.org and register for a free sip account
2) go to ipkall.com and use your iptel info to register your sip account with ipkall
3) download jitsi softphone
4) enter your iptel.org login info under sip
5) create a google voice account
6) have google voice verify your ipkall phone number

Additional steps: may or may not be needed 

open a terminal window and type: sudo apt-get install apache2 
                       then type: supd apt-get install mysql-server
                       then type: sudo apt-get install php5
                    then type sudo apt-get install libapache2-mod-php5
                      
                                  then install openfire
                       
reboot

now go into your web browser. In the address bar type: [http://localhost](http://localhost)

install the jinglenodes plugin

reboot

next, in jitsi, go to tools > Options

head over to the audio tab

make sure only PCMU/8000 and telephone-event/8000 are selected

under video, deselect all encodings

go back to the accounts tab and select your iptel.org account

select Edit

under the connection tab, select Register as the Keep alive method
Change the keep alive interval to 25

go to the security tab, and deselect "Enable support to encrypt calls"

under Presence make sure Enable presence and force peer-to-peer presence mode are selected

click next

then select login from the summary page. 

NOW- head back over to your voice.google.com account
login
press the call tab
enter a phone number of your choosing
press call me

should ring to your computer. if not, something went wrong... Re-read this guide and follow all steps as described, exactly. Pay more attention to what you read.

---

