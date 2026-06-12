---
title: "At the END of my rope with Thunderbird"
date: 2012-04-28
forum: General Help
---

### Post by r_avital on 2012-04-28
I have been using Thunderbird for ages.  Recent upgrade (from repositories) to version 11.0.1 broke everything.

Ubuntu Lucid 10.04 64Bit, initially installed TB from repositories, then a recent update-manager popup came up with TB upgrade, and I always trust the repositories, so I upgraded.

This morning I noticed that my Gmail inbox in TB was not receiving new messages that clearly showed when I logged on to gmail.com (with Firefox).  Tried to download messages via TB, long hourglass.  Gave up.

Removed the account, tried to recreated it.  Verified that all the parameters were correct, did an auto-create, got the following message:

```

[Exception... "Component returned failure code: 0x8000ffff 
(NS_ERROR_UNEXPECTED) [nsIMsgIncomingServer.verifyLogon]"  nsresult: 
"0x8000ffff (NS_ERROR_UNEXPECTED)"  location: "JS frame :: 
chrome://messenger/content/accountcreation/verifyConfig.js :: verifyLogon :: 
line 130"  data: no]

```Tried again, this time I got a message reading that the server already existed.  It NEVER showed up in the TB pane.

Found some article on the internet about running the config. editor, so I did, following the advice, I filtered on "hostname" and sure enough I found the mail and smtp servers.  I blanked out the entries, tried to create the account again, with same results as above.

Uninstalled and reinstalled TB via Synaptic about 5 times.  Same results.

This does not seem to be related to gmail specifically, because I have another (webmail) account that was also working perfectly for years, within TB, and it has the same problem.

Please, please, if anyone has any ideas about this, I am right now without a working email client.  I would hate to have to abandon TB.

And a warning to others, DO NOT upgrade to TB 11.

Thanks in advance

---

### Post by QIII on 2012-04-28
You should have warned me about TBird 11.0.1 before I upgraded and it actually worked.

Be careful about assuming that your experiences are the same as others' or that they will encounter the same problems as you.

You could try moving your profile (keep it so you don't lose your mail) outside of the .thunderbird directory and restarting Thunderbird.  (Your current profile is /home/yourname/.thunderbird/somerandomcharacters.default)   Simply uninstalling will leave that profile and any problems caused by it will just show up again.

If you are able to start it and set it up, move your current mail into the new profile folder.

---

### Post by r_avital on 2012-04-28
Thanks, I did move the profile back and forth.  Same results.

Speaking of profile, starting TB at the command line: thunderbird -ProfileManager  or thunderbird -P - this simply opens up TB, NEVER opens up the profile manager.  Never.  It did before.  Doesn't now.

Another strange behavior:  Uninstalled TB, Enigmail, TB-gnome-support, several times, every single time I took care to specify a COMPLETE removal, including config. files (should be the equivalent of "purge" on aprt-get, right?) - and when I reinstall, I have no accounts, I can't create acounts, but ALL my addons are there.  A profile directory is created under my .thunderbird folder, it's supposed to have a random string + your unsername as a folder name (e.g. er46zx.joesmith) - but it's EXACTLY the same name, exactly the same "random" portion in the name.  So "complete removal" or "purge" doesn't really work with TB?

I would be happy to be able to start from scratch with a new profile, but I can't even do that.

And you're correct, I shouldn't assume, because on my end it worked fine for about a week or so.  Still wish I'd never done this %$#@! upgrade.

Thanks, at any rate.

---

### Post by QIII on 2012-04-28
I'm still looking around, but it seems that at least some people have gotten around the verification issue it appears you are getting by doing one of two things:

1.  Going to gmail directly and changing your password, then reconfiguring your Thunderbird profile.  It seems that some people are finding that something is causing gmail to suspect something is wrong and raise the CAPCHA, which you aren't seeing.

2.  Changing Thunderbird setup from IMAP to POP3 or vice versa.

Still looking for the profile thing.

If neither of those things work, it might be worth trying the 12.0 Beta (and I'm sure you understand that betas can be troublesome) to see if it really is something about 11.0.1

[http://www.mozilla.org/en-US/thunderbird/channel/](http://www.mozilla.org/en-US/thunderbird/channel/)

And remember, YMMV.  We're trying to nail down the problem here.

---

### Post by r_avital on 2012-04-28
Thank you for your help.  No joy though.

1. Changed password on gmail.com, tried to recreate the account in TB - same behavior as before.

2. Attempted to create pop account (after reinstalling TB from scratch) - same "exception" error as before and when I try again, "incoming server already exists" - at NO time does anything show in the accounts panel other than "local folders"

3. Your link actually took me to a version 13 Beta, installed that (untarred to local folder) - same exact behavior.

But you know what?  Every single time, all my addons are installed.

Something from a previous, broken installation never gets removed, even when I purge.

I'd love to know what that is.

P.S. also found info on gmail about unlocking captcha, and I unlocked it, but still getting the exception error above.

I am not sure this has anything to do specifically with gmail, since the same happens with my other email provider.

P.S. More info
I just installed TB, Enigmail, and Thunderbird-gnome-support packages on a completely separate machine, which is also running Lucid 10.04 64Bit.  Installation and connection to servers, creation of accounts, was flawless.  It runs the profile manager pretty as you please.

However, this is a machine that I rarely use, not powerful, and I really need to resolve the problem on my "main" machine.  The success I've had above with the alternate machine tells me there is something on my "main" machine, the one that has the problem, that is definitely keeping some bad info on previous installations.  I need to find out what that is and blow it away so I can make a clean install of TB.  If anyone has any ideas as to what that might be, please, please let me know.

Thanks again.

---

### Post by JKyleOKC on 2012-04-28
On my 10.04.4 system, upgraded to TBird 11 and thence to 12 via the update manager not long ago, I find four different directories that can contain configuration data. One is /etc/thunderbird, which on my system contains only three lines, all of which are commented out. The other three are all hidden directories in my home directory: .mozilla, .mozilla-thunderbird, and .thunderbird. The first appears to be the configuration file for Firefox and I see nothing there related to TBird. The .mozilla-thunderbird entry is simply a symlink to .thunderbird; apparently the name changed somewhere between version 3.6 and version 12.

I would try renaming the two definitely-related TBird files in your home directory to something else such as .m-badbird and .badbird, then launching Thunderbird again. This should cause it to re-create a hidden configuration file; of course all of your preferences would be wiped out, as would your add-ons (which are listed in the *.defaults subdirectory), but the problem should go away. You could then copy items from the .badbird or .m-badbird directory to the newly created one, one at a time, to determine which one contains the bad info...

I would also look at the /etc/thunderbird directory, and possibly rename it also if it contains any active lines.

Hope this helps; it's definitely the long way around but should lead to success eventually.

---

### Post by sgage on 2012-04-29
TB 11 working perfectly here. I am using the POP3 mode of Gmail. 

I would save my mail store, delete ~/.thunderbird, sudo apt-get purge thunderbird, then sudo apt-get install thunderbird.

---

### Post by r_avital on 2012-04-29
Solved.

My apologies to all for my own bozosity.  And thanks to all for the useful suggestions - I had already tried moving/deleting the ~/.thunderbird folder before I posted, I try not to post questions before I do a lot of troubleshooting and research on my end.

Long story sort, every time I reinstalled TB from scratch (via synaptic or apt-get) - I always made sure I purged TB before reinstalling, yet every single time, even though there were no accounts and no possibility of creating accounts, all my extensions were there.  This got me thinking, and I started removing extensions, three at a time before restarting TB and removing more.

Well, after removing the first three, TB launched without any extensions.  Uninstalled/purged, and installed again.

First, thunderbird alone.  I knew this was right because the first thing I did was run it with the -ProfileManager switch, and this time it finally ran the profile manager as it was supposed to.  Created a profile, then installed thunderbird-gnome-support.  Restarted again, created accounts successfully (somehow, the auto-create process "thinks" gmail is "googlemail.com" when it is in fact "gmail.com" but that's a minor fix).  Then installed the enigmail package (from synaptic), restarted, success.  Installed all the xul-lightning and google-data related packages (again, from synaptic), everything is still fine.

What probably happened:  Every TB user who cares enough about the extensions they use, are forced to "cheat" by adjusting the minversion and maxversion parameters in the install.rdf file of every extension, since TB upgrades every 15 minutes and makes their extensions obsolete.  You work on your email client to add value to it, and it never lasts very long, so you "cheat" that way.  Probably one of the extensions created a problem that affected the functionality of TB.  I found updated versions to most of my extensions.

[aside: The only one where I'm still forced to cheat with the maxversion parameter, is clamdrib, which allows ClamAV to scan every email for viruses.  It is completely silly that the TB developers get so animated defending the decision to put tabs above toolbars from now on, but after so many years they still can't come up with a reliable way to provide virus scanning to TB.  End of rant.]

Again, thanks everyone for your help :)

---

