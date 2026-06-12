---
title: "Weather updates to email (plus a few more things)"
date: 2011-08-10
forum: General Help
---

### Post by W@@dy on 2011-08-10
Last night I discovered email and SMS are basically synonymous.

So I've schemed up an idea I REALLY want to do, but I need help figuring out exactly how/what programs to use.

What I want is Weather updates to be downloaded or emailed to my homeserver, it doesn't matter which.

Then I want to be able to request updates from my phone whenever I want.
I know it's already possible and extremely easy to just have weatherchannel send SMS updates to my phone, but I don't want updates set to a schedule where they _always_ arrive every day or whatever.
I want to request them on my whim.


So my thought was to have weatherchannel (or some other weather forecaster) send an email account (I can set up a new one dedicated to it) the updates and then download them to my home server, or I could download RSS updates to the server (I couldn't figure out how to find the location of the RSS downloads using Liferea though)

I've already tested texting my email account, which works of course, so I know it's possible for my home server to receive my "requests".

I've already set up and tested "Mutt" with my current gmail account so my home server can send out the weather updates by sending out the weather text file and sending it via a script.

Now all that's left is to figure out how to make the server "Read" any email requests I send it (with a keyword I'd make up like "Weather Update"), and then activate a script to email my phone back with the latest weather update text file.
So how can I make a script to read emails? Do I need to reach outwards into a programming language, like Python or something?

Any help would be appreciated.
If this is possible with weatherchannel already, I'd still prefer to do it this way, just for sake of learning scripting and a bit more about ubuntu.
I'm still learning, and loving it more everyday :o

---

### Post by Habitual on 2011-08-15
W@@dy:

check out rss2email. It's awesome! I use it to get any/all rss feeds that I need delivered to my local mail spool.
Thunderbird is what I use but any mail client should also work too.

On your "homeserver"...

Terminal > ```
sudo apt-get install rss2email
```

As your usual/regular user in terminal >
```
r2e new woody
``` I'm using woody here, but substitute your login name/ID if appropriate.

then in terminal:```

r2e add http://myweatherrss_address.com

```

Setup Thunderbird with these settings:

Edit > Account Settings > Account Actions button > Add Other Account
"Unix Mailspool" > "Your Name" (name) > "eMail Address" (woody@localhost)
"Use Global Inbox" checked or unchecked. it doesn't seem to matter.
"Account Name" (feeds)
Finish > OK

Another email client may have similar settings but most can be 'faked' (possible exception is "woody@localhost") with arbitrary info since you wont' be sending off this account.

still in terminal >
```
crontab -e
``` and add
```
*/5 * * * * /usr/bin/r2e run
```

This will retrieve rss weather from [http://myweatherrss_address.com](http://myweatherrss_address.com) every 5 minutes and stick in your email client.

I am subscribed with interest to this thread.

Please let me know.

---

### Post by W@@dy on 2011-08-16
Hey thanks for the response!

The RSS Feed is the one part I was actually clueless on, so that will definitely help me, thanks!

Right now I'm working on making a python script.
It works if I enter it line by line into the IDLE python shell (its like a terminal for python, my terminology could be off since I'm new to it).
But if I save it as a file it won't work for some reason :l

It says that 'os' in "os.system()" and "os.remove()" is a syntax error,
and I did put 'import os' at the top.
I'm baffled why it says this since it works when I manually enter it line by line.


Other than that though, it read the email file, and sent a text back to my phone successfully :D so just gotta iron out that bug, then work on receiving the RSS Feed

---

### Post by Habitual on 2011-08-16
rss2email is python. ;)

I don't know jack about python, although it looks to be plain "Chinese", I mean English. I haven't dived into it.

---

### Post by W@@dy on 2011-08-17
Okay I've got the python script fixed, so now I'll spend tonight working on the RSS Feed, and make a new dedicated email account.
After that I'll have to fix up how emails are stored to my PC. Right now I have to manually view the email using Mutt before it's stored to my PC.

---

### Post by W@@dy on 2011-08-18
Okay I'm having a bit of a problem.

I setup rss2email and crontab as you said, didn't have any issues there, no errors popped up.

However setting up thunderbird raised issues (I decided to move away from mutt for the simplicity of having a GUI)
I setup a second account called Weather_Update and with the same settings you provided.
However it's unable to retrieve any email because it cannot find the Mail Spool File.
I looked into settings and it has 3 options under "Copies and Folders" which are "Weather_Update", "Local Folder" and "Ydoow111@gmail.com" which is my main email account.

I tried searching through the thunderbird folders (/home/woodams/.Thunderbid) but couldn't find anything labeled "Weather_Update"
I'm not very familiar with how programs place their folders or files in ubuntu though. That's something I've been scratching my head over for weeks now; I just can't seem to figure it out :l

---

### Post by Habitual on 2011-08-18
Check your email. ;)

---

### Post by W@@dy on 2011-08-18
Yeah that's what I did.

I rechecked everything and found out I had the wrong URL for the RSS Feed. I fixed that, and still having the same issue though.
I installed "Scheduled Tasks" so I could have a better visual of what tasks were in Crontab, and confirmed that it was running rss2email every 5 minutes.
I remade the second email account just to be sure there weren't any mistakes.
Waited approx. 15 minutes to ensure r2e was run at least once, then I click Check Email in Thunderbird and it says "Can't find Mail Spool File"
Only for the newly created Account

Here's my question, how does r2e know where to send the email?
It's run every 5 minutes, and downloads the RSS Feed, but I didn't provide it with any email to send it to, so how will that email account receive it?

I'm a noob when it comes to email servers and such. This is my first time having a reason to delve into how it works

---

### Post by Habitual on 2011-08-18
see my reply where I said "I'm using woody here, but substitute your login name/ID if appropriate."
So now, another method... terminal >
```
r2e new $(whoami)
r2e add http://myweatherrss_address.com
r2e run
mail

```

Whatever name you Log in as, that is where your rss feeds will 'go'.

when the rss2email process works correctly (indicating you have setup and added a new rss url correctly) you can simply type (in terminal, at any time) "r2e run" and then "mail" in a terminal.

re-read my original reply carefully. ;)

you can "test" your mail spool and/or email client by issuing this in terminal:

```
mail -s rsstest $(whoami)
Hello World <press enter>
**.** <press enter>
mail
```

an email should show up with the subject "Hello World" and this test email should also be present in your email client under the rss account you setup.

[rss2email homepage](http://www.allthingsrss.com/rss2email)

---

### Post by W@@dy on 2011-08-19
I did use my login name for r2e, which is woodams. Unless I accidentally capitilized the 'w'

I can't get to the comp right now, but I'll definitely try what you posted when I can sometime tomorrow and reply with what happens

---

### Post by Habitual on 2011-08-19
ok!

---

### Post by W@@dy on 2011-08-21
Alright here's a few things I did

Copied from Terminal:
```
woodams@woodams-PineTrail:~$ r2e list
default email: woodams
1: http://rss.weather.com/weather/rss/local/14020?cm_ven=LWO (default: woodams)
woodams@woodams-PineTrail:~$ whoami
woodams
woodams@woodams-PineTrail:~$ mail
Cannot open mailbox /var/mail/woodams: Permission denied
No mail for woodams
woodams@woodams-PineTrail:~$ sudo mail
[sudo] password for woodams: 
No mail for root
woodams@woodams-PineTrail:~$ r2e run
woodams@woodams-PineTrail:~$ sudo mail
No mail for root
woodams@woodams-PineTrail:~$ 
```So unless I'm mistaken, that confirms R2E is setup correctly with the correct username?
I did try letter for letter what you told me to do, with the same result. I posted this because I felt it gave better feedback as to the settings of r2e.

Next I checked out the Folder Settings of Thunderbird.
Thunderbird has the inbox and other folders under /home/woodams/.Thunderbird/51566dgc.default/Mail/localhost-1

it's "-1" I believe because this is the second localhost account I made; I deleted the first as a part of troubleshooting.

Inside that folder are all the Inbox and Inbox.msf (which as I understand it is the mail spool file) and other folders. They look proper.
Thunderbird is pointed to that folder.
I also tried the "Repair .msf files" option in Thunderbird.

It still gives me the "Mail Spool File could not be located" error :?

I tried to send a Test Email, as you said, but it never sent the mail, or perhaps I don't understand what's going on.

```

mail -s rsstest $(whoami) 
Hello World <press enter> 
**.** <press enter> 
mail
```After typing "mail", the final line,
nothing seems to happen. I get another line to type in letters. The terminal sits there like I should do something else. It doesn't close, or say "Mail sent".
Just sits there...

Oh, at first I didn't have the package for the 'mail' command, so I installed mailutils.
That MAY have something to do with it, however I am not sure.

Finally, I checked the /var folder for any mail folders because I felt like that's where the mail was supposed to go in the first place after reading around the interwebz.
There's a /var/Mail folder, with a file named 'root'
and there's a /var/Spool folder with a "Mail" Folder link under 'Spool'

I'm trying to give you as much info as I can because I have absolutely no idea what's wrong lol

---

### Post by Habitual on 2011-08-24
```
sudo touch /var/mail/woodams
sudo chown woodams:mail /var/mail/woodams
```

will fix the "Cannot open mailbox /var/mail/woodams: Permission denied" issue.

Your r2e list looks correct.

This should fix you right up.


forget about```
 
mail -s rsstest $(whoami) 
Hello World <press enter> 
. <press enter> 
mail
```

---

### Post by W@@dy on 2011-08-24
Hm. So you think Thunderbird couldn't find it because it didn't have appropriate permissions?

I'll try this in a few hours and post back

Thanks for your help, I really appreciate it. Like, a lot.

---

### Post by Habitual on 2011-08-24
> **W@@dy said:**
> Hm. So you think Thunderbird couldn't find it because it didn't have appropriate permissions?


That is my guess, yes.

You should be golden now/soon.

Subscribed with interest!

---

### Post by W@@dy on 2011-08-24
No error! But it didn't report any mail either. So I'll wait about 10-20 mins (just to be sure) and report back again if any mail has filled up.

But yes, it's now able to find the mail spool file it would seem

---

### Post by Habitual on 2011-08-24
2 things to try:
```
r2e run
``` as woodams

and/or send a test email from terminal>
```
mail -s rsstest woodams
```

it will come down to a blank line and wait... enter "Hello World" (without the quotes)  and press <enter>, then type a period on a new line and press enter again. Message sent to your local mail spool.

Use the "Get Mail" button in Tbird.
an email with subject rsstest should pop into your inbox.
Did you set a cron for "r2e run"?

Lemme know...

---

### Post by W@@dy on 2011-08-24
D: nothing showed up.
I feel like settings are off, or target directories are off, but I can't get a sense of what should go where even after looking at guides >_<

I can't get the terminal to send the account an email. I'm following your directions to the letter, but the terminal doesn't send the mail after the "." and I press enter.
It feeds me another blank line to type into. If I press Ctrl+D it says it can't parse the message because the message is still being expanded, which to me means it's still being written to, correct?
If I press Ctrl+C it asks me to press Ctrl+C again to confirm the cancellation, and that the message WONT be sent.
This is all after I press ". <enter>"

I'm never this bad at tech stuff, I swear

---

### Post by Habitual on 2011-08-24
It's probably smth simple. Don't give up, you are 99% of the way there.

mail -s rsstest woodams <enter>
Hello world <enter>
. <enter>
EOT
You have new mail in /var/spool/mail/woodams
is what you should "see"

---

### Post by Habitual on 2011-08-24
> **W@@dy said:**
> ...the terminal doesn't send the mail after the "." and I press enter.
It feeds me another blank line to type into

Try another period <enter>

---

### Post by W@@dy on 2011-08-24
I know I'm 99% of the way there, and that's the most frustrating part! lol

The extra  . <enter> did not work either
nor did 50 of those thereafter XD
nor double '..'

I fiddled around with the extras too (extras means -> -s, -u, etc. etc) and that didn't work either.

---

### Post by W@@dy on 2011-08-24
I'm throwing this out there, just because I want to give you as much info as possible.
On the second account, called WeatherFeeds, Thunderbird has it using my other account's SMTP settings for outgoing mail.
Secondly the "Local Directory" under "Server Settings" for this account was set to /home/woodams/.Thunderbird/*numbers I can't remember*/Mail/localhost-1

I changed it to /var/spool/mail to see if that did anything (and it made sense to me), but still didn't reveal any emails.
I checked var/spool/mail and it does show 3 files
root
woodams
Inbox

none of those have any extensions, which is beyond bizzarre coming from Windows :P

I can change the local directory back under thunderbird if that was a bad move. I made sure I knew the old location before changing

---

### Post by Habitual on 2011-08-25
Woody:
mail account for Inbox is an errant mailbox, you can safely ignore it for now.

Using the mailutils package binary of mail here gave me the same symptoms as you described, so I suggest removing it and installing heirloom-mailx using these 2 commnads:

```
sudo apt-get remove -y mailutils
sudo apt-get install -y heirloom-mailx
```

NOW these commands should work:
mail -s rsstest woodams <enter>
Hello world <enter>
. <enter>
EOT

then verify/reconfigure Tbird:
Tbird settings for verification (or re-setup) of the Tbird account.
Edit > Account Settings > Account Actions button > Add Other Account > "Unix Mailspool" > woodams > "eMail Address" woodams@localhost

"Use Global Inbox" checked or unchecked. it doesn't seem to matter.
"Account Name" (WeatherFeeds)
Finish > OK

I sent you an email to the Ydoow111 account you posted on page 1 of this post to assist you getting this up and running.
Forum communication is sometimes difficult. We seem to both be EST. :)

Please let me know.

JJ

---

### Post by Habitual on 2011-08-25
> **W@@dy said:**
> ...Thunderbird has it using my other account's SMTP settings for outgoing mail.

That's expected, but you will never send mail using Tbird on the WeatherFeeds account, so it doesn't matter that Tbird "thinks" the outbound email server is. :)

---

### Post by W@@dy on 2011-08-26
Okay I did that, and the steps now work, sweet.

However it still reports no mail; in ThunderBird and by typing "mail" into the terminal.

If you think folders, or permissions got WAY screwy for whatever reason and I need to start over with a fresh install, I can do that. Don't be shy lol.
I've been testing all of this on a netbook, so it's no big deal, and I have a flash drive to back up all the important things I want saved.

---

### Post by Habitual on 2011-08-26
Woody:

Lemme get this straight, you did a "mail -s" command and sent yourself and email from c-li and the mail c-li command doesn't show it?
"No mail for woodams" is the response from mail in terminal?

Fresh install not necessary, all you could do is delete the WeatherFeeds Tbird account in Tbird and start over from that point.

You didn't answer my question about setting the cron...?

You could also add another rss feed from terminal > 
```
r2e add http://status.aws.amazon.com/rss/all.rss
```
Any valid rss feed url will suffice, I just know this one off the top of my head.

Then issue an ```
r2e run
``` from terminal, then "Get Mail" button in Tbird.

What a hassle, I had this working inside 15 minutes.
Not a reflection on you, I'm just saying it is not normally this problematic.

JJ

---

### Post by W@@dy on 2011-08-26
Last I checked, there was a cron job setup, and it was set to 5 minutes. I was using the program "Scheduled Tasks" which gives you a pretty straightforward GUI of cron jobs as well.

That is correct that I sent myself an email from Terminal.  I did the mail -s rsstest woodams
and I also did r2e run

The netbook is dead atm, and the charger is across town, but when I get it I'll try a different rss url, delete the Tbird account and try again. I'll also delete, and recreate that cron job just to be sure.

I think this is why I never got into email-oriented things. Anything even somewhat relevent to Networking and internet decides not to work for me lol.

---

### Post by Habitual on 2011-08-26
ok, I'll wait for a re-charged update from you later. 

Have a Great Day!

---

### Post by W@@dy on 2011-08-26
Alright I remade the cron job with 'Scheduled Tasks', it reads as follows (according to the gui)
"At minute: */5, every hour, every day of month, every month" it runs /usr/bin/r2e run

That's how it reported the original cron job I created which was a copy and paste of what you posted. So that should be fine.

I deleted the Tbird account, haven't recreated it yet.

I reset r2e. I changed the default email from 'woodams' to 'woodams@localhost', just to see what happened when I typed "r2e run". Nothing did.
Then I tried my gmail account, it didn't send anything out either.

I checked both links, the one you provided and my own, through a web browser and those checked out. Currently both are attached to r2e with my gmail account.

So, it seems like emails aren't getting sent, right? My first instinct was to blame 'R2E', but I'm also not receiving emails when I send them through terminal. So maybe it's something within the OS?
I'm not really sure, just throwing darts in the dark lol

Edit: I checked around, and I do have Postfix installed, which is a type of sendmail. Although I can't figure out the arguments for the commands, and the commands require root permissions (sudo).

---

### Post by W@@dy on 2011-08-28
Here's my question.

In /var/mail/ the local mail should get stored under a file named after my username correct?
There's two files, does it get stored under "username" or "username.msf" ?

I want to see if I can make a fake email to see if it will report that. Perhaps that will tell us if the message is just failing to be sent, or failing completely.
I'm really confused as to why this part won't work. I've been hounding online tutorials everywhere, and no one seems to be having this issue

---

### Post by W@@dy on 2011-08-28
I just uninstalled Postfix (which I learned is an MTA, Mail Transfer Agent)
and replaced it with SendMail, another MTA

```
woodams@woodams-PineTrail:~$ mail
Heirloom mailx version 12.4 7/29/08.  Type ? for help.
"/var/mail/woodams": 1 message 1 new
>N  1 The Weather Channe Sun Aug 28 15:51   24/1214  Your 10-Day Forecast for 
? 

```Does this mean I do the happy dance?

Edit: Thunderbird account is now showing all emails for local email, including a 'TEST' email I sent myself with the same process you provided me earlier.

---

### Post by Habitual on 2011-08-28
The Weather Channe Sun Aug 28 15:51   24/1214  Your 10-Day Forecast for

is a GREAT sign and it's a "We have liftoff" moment.
That same email should also show up in Tbird using the WeatherFeeds tbird account.

.msf files "may" be a remnant of that other mail agent (before mailx, exim maybe?)

I set this thing up several times on several OSs including Ubuntu using the steps outlined at [http://www.linux.com/archive/feature/50469](http://www.linux.com/archive/feature/50469)

Lemme know...

---

### Post by W@@dy on 2011-08-28
Yep, it's showing all emails, including rss2email. Idk why I didn't mention that in the first post. I guess I got so excited I forgot to mention it lol.

It looks like the emails are VERY well formatted for what I'm trying to do.
I was afraid the emails would have a giant list of text, or images and other things attached. But from what I can tell, I could probably just forward that entire email to my phone as-is.
I won't though, because I want to touch it up a hair.

Next step is to check where the emails are being stored (hopefully in separate files) and change my python program to read them

---

### Post by Habitual on 2011-08-28
Glad to hear it all worked out.

---

