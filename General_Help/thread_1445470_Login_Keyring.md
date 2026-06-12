---
title: "Login Keyring"
date: 2010-04-02
forum: General Help
---

### Post by Xorlathor on 2010-04-02
Whenever I boot up my computer, Ubuntu (10.4) brings me to my desktop, then immediately displays a prompt to enter my login keyring. After some searching on the forums, it appears that this is because I set my laptop to auto-login.

Am I missing something here, but what does auto-login have to do the the keyring? Why do I even need to enter that password? I understand that many Ubuntu users are picky about security, but why isn't their any option to disable this? It's almost as bad as UAC from Vista, which is one of the reasons I'm dual-booting Ubuntu in the first place. 

This is an annoying "problem" that has been bugging me since I first installed Ubuntu - how can I change it?

---

### Post by Johnny B on 2010-04-02
this has nothing to do with auto login. the keyring is most likely for a secured wireless connection, just set the keyring password to be blank. 

you can change the password with this:
[http://ubuntuforums.org/showpost.php?p=2091209&postcount=4]("http://ubuntuforums.org/showpost.php?p=2091209&postcount=4")
OR
[http://ubuntuforums.org/showpost.php?p=943443&postcount=7]("http://ubuntuforums.org/showpost.php?p=943443&postcount=7")

---

### Post by burton247 on 2010-04-02
You can disable it. It's to allow nm-applet to run. When you first connected to the network ubuntu would've asked you to set a keyring password. Third time around i left it blank and it doesn't ask me for one anymore. Don't know how to disable it off the top of my head but I'm sure i can find out

[edit]

I got beaten to it, but I'll leave my post up anyway

---

### Post by rascalbear on 2010-04-05
i am trying to get my keyring password also but tells me the file is of a unknown type? What else could i try?

---

### Post by bahularora on 2010-05-19
hey, guys i am using Ubuntu 10.04 , I encountered the same problem. I think the simplest way is to go to  

Applications>Accessories>Password and encryption keys.

The Password and encryption keys window will open , you can rright click on the "**Passwords**:login" select last option "change password" and change it..... i.e. make it same as your login password.  I did that and its not asking for the keyring password now!!

---

### Post by xtopher.brandt on 2010-09-09
You can also delete the Login keyring from the context menu. This is what you need to do if you've forgotten (or don't remember ever setting) the login keyring password.

---

### Post by richard.scott-ettrick on 2010-10-17
I don't like the new version. When using Firefox quite often the scroll bar won't work and also quite often freezes up totally. You then have to wait a while to let it unfreeze itself. Anybody any ideas whats going on?

---

### Post by richard.scott-ettrick on 2010-10-17
OOPs! Wrong Topic! Shouldn't have posted previous comment here!

---

### Post by Peter Wagner on 2010-11-08
Hello,

just to say that copying the password in the login section didn't help. But it seems I have a different problem linked to Ubuntu One: When I unchecked my computer in Ubuntu One I don't get the password request right after login, but after a strat of Firefox. There should be no connection to the netwqork manager, as this doesn't happen when I download mails via Thunderbird.

Peter Wagner

---

### Post by HippieDave on 2011-07-28
This thread is pretty old, but it doesn't ever really address the problem.  At log in, but also periodically when the system is up, I get a request for my "login keyring'.  I left the system set up with no pass word log in (i.e. auto log on).  Can I get rid of this annoyance?

---

### Post by thirumale on 2011-09-10
> **Johnny B said:**
> this has nothing to do with auto login. the keyring is most likely for a secured wireless connection, just set the keyring password to be blank. 

you can change the password with this:
[http://ubuntuforums.org/showpost.php?p=2091209&postcount=4](http://ubuntuforums.org/showpost.php?p=2091209&postcount=4)
OR
[http://ubuntuforums.org/showpost.php?p=943443&postcount=7](http://ubuntuforums.org/showpost.php?p=943443&postcount=7)



Thank u.... it works....

---

### Post by cliff0108 on 2011-10-17
Yes - someone please help
I keep getting this stupid "loginkey ring" message and as well, although I opted for automatic login it keeps asking me for my password.
I know about security etc etc but I find this password stuff totally annoying and I have NO need for it.
Thanks
Cliff

---

### Post by gandaran on 2011-10-17
> **cliff0108 said:**
> Yes - someone please help
I keep getting this stupid "loginkey ring" message and as well, although I opted for automatic login it keeps asking me for my password.
I know about security etc etc but I find this password stuff totally annoying and I have NO need for it.
Thanks
Cliff
use a blank password when setting up the keyring choose the unsecured way, it wont bother you anymore asking to enter password.

---

### Post by afwings on 2011-10-19
The second link worked for me; thanks! I had just upgraded to Ubuntu 11.04 and was trying to open a Ubuntu One account. Started getting the password messages described earlier in the thread.

So I'm just reporting that the procedure here [http://ubuntuforums.org/showpost.php?p=943443&postcount=7](http://ubuntuforums.org/showpost.php?p=943443&postcount=7) still works with 11.04.

---

### Post by andrewhg on 2012-01-05
For Ubuntu 10.04 here is an easy solution copied straight from the user manual. 
*


"You may be asked for a password every time you log in so that you can connect to a network. You can stop this from happening like so:
  

1.Right click the Network Manager icon and choose 'Edit Connections'.
2.Go to the 'Wireless' tab, select the connection you are using and click Edit.
3.Check 'Available to all users' and click 'Apply'. Enter your [administrator] password when asked.
          
The next time you log in, you should not need to enter your password in order to connect to your network connection"

---

### Post by kayas80 on 2012-01-27
> **andrewhg said:**
> For Ubuntu 10.04 here is an easy solution copied straight from the user manual. 
*


"You may be asked for a password every time you log in so that you can connect to a network. You can stop this from happening like so:
  

1.Right click the Network Manager icon and choose 'Edit Connections'.
2.Go to the 'Wireless' tab, select the connection you are using and click Edit.
3.Check 'Available to all users' and click 'Apply'. Enter your [administrator] password when asked.
          
The next time you log in, you should not need to enter your password in order to connect to your network connection"

That worked for me, thanks.

---

