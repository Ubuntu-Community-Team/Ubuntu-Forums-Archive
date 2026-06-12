---
title: "I don't want Chrome"
date: 2011-05-18
forum: General Help
---

### Post by ewaynec on 2011-05-18
My OS (Lucid) came with Chrome. I removed it. I installed Mediatomb, it installed Chrome. I removed both. Every time I get updates it has Chrome included. I un-check it (telling it not to install). It installs it anyway. It is not hurting anything being there, It is a little unsettling that Ubuntu is so persistent in installing it without regard to me saying I do not want it. Is there any way to stop this?

---

### Post by Blasphemist on 2011-05-18
You should be able to remove it by removing the package source from your system using symantic package manager. I have natty and chromium but the package should be something like=
LP-PPA-chrome-daily-stable/lucid

You are on 10.04 which is the current long term support release so there isn't really a need to upgrade just yet though like I said I have. Also, I use chromium as my default browser. Chrome is just as good as long as you have it set not to send data to google. IMO

---

### Post by JOHNNYG713 on 2011-05-18
firstly, if you are running Lucid Why are you having Ubuntu 8.04 in sig? secondly, Go to software sources and remove the chrome repository and or install Ubuntu Tweak, and remove Chrome from there, along with purging the repo !, Responders PLEASE read the entire post and respond accordingly ! :P Thirdly, Be wary of upgrading to natty, as there are and is, MANY faults ! best at this point to stay with Lucid, Unless you are a tester ! Fourthly !? What is the issue with Chrome? just askin as Firefox 4 mimics inmost respects Chrome !and what is your preferred browser,? As to get a better idea of where your needs are !?

---

### Post by michaelzap on 2011-05-18
> **ewaynec said:**
> My OS (Lucid) came with Chrome. I removed it. I installed Mediatomb, it installed Chrome. I removed both. Every time I get updates it has Chrome included. I un-check it (telling it not to install). It installs it anyway. It is not hurting anything being there, It is a little unsettling that Ubuntu is so persistent in installing it without regard to me saying I do not want it. Is there any way to stop this?

Your post perplexes me. First of all, Lucid does not come with Chrome (it comes with Firefox). Secondly, as far as I can tell (having never used it) mediatomb has nothing to do with Chrome either. Did you or someone else perhaps install Chrome on your own at some point, and have you perhaps not uninstalled it (using Synaptic is the easiest method)?

---

### Post by ewaynec on 2011-05-19
I'm kinda sorry I asked. I have what I consider, not a problem, but a question. 
  Blasphemist; I said in the original post that I removed it, I never said I wanted to upgrade. I don't care if Chrome is better than Firefox.
  Johnnyg713; 8.04 is what I was using when I filled out that info.As I said I have removed it several times. I have no problem with Chrome, I just don't use it.
  michaelzap; I may have mis-spoke about Lucid coming with Chrome, but the first thing I do with a new install is download the updates, and there it is. Mediatomb does install Chrome as it's browser, you can't install it without Chrome. I am the only user on my machine, I have never (knowingly) installed Chrome. Yes, I removed it with Synaptic.
  I don't want to sound unappreciative, but I have on several occasions asked a simple question and get a lot of responders who offer only more questions or answers to questions I did not ask.
  So, now I have tried to answer all of your questions, will someone try to answer mine, Thank you.

---

### Post by uRock on 2011-05-19
In what manner did you remove Chrome? You should open software sources and remove Chrome's repository. To get to Software Sources, open Ubuntu Software Center, then click Edit, then select Software Sources, then you can either uncheck or completely remove the Chrome repository. (All three posters did offer help with that.)

Once the software and PA are removed, the system shouldn't offer to install Chrome again in the future.

---

### Post by michaelzap on 2011-05-19
> **ewaynec said:**
> So, now I have tried to answer all of your questions, will someone try to answer mine, Thank you.

The reason for the questions (along with the helpful advice) is that Chrome is not part of Ubuntu's standard software and it will not install itself. So you must be misunderstanding or misstating something. The only way to just answer your question is to say that what you're describing is not possible, but by asking questions we can be more helpful than that. ;)

I suspect that you installed Chrome via mediatomb (if, as you say, it requires Chrome). If you uninstall mediatomb and Chrome in Synaptic or the Software Manager, they will not come back on their own. Note that there are two versions of the Chrome browser (Chrome from Google and Chromium which is the open source version), so perhaps you have both but only uninstalled one?

---

### Post by ewaynec on 2011-05-19
uRock; as I said before, I used Synaptic to remove it. There is no repository for Chrome. There is one for Google. If I do as you say I must remove the Google repository, and I do not want to do that.

michaelzap; maybe you are misunderstanding what you are reading. I never said it is installing it's self, and I never said it is coming back on it's own. Did you read my original post? I can't explain it any better.

  Maybe I missed something somewhere and did not tell it I did not want it.

---

### Post by uRock on 2011-05-19
When you install MediaTomb and it adds Chrome, then you remove Chrome, does it uninstall MediaTomb as well?

---

### Post by ewaynec on 2011-05-19
> **uRock said:**
> When you install MediaTomb and it adds Chrome, then you remove Chrome, does it uninstall MediaTomb as well?

I don't know.

---

### Post by lithopsian on 2011-05-19
Mediatomb requires a browser package to be installed.  Firefox is acceptable, as is Iceweasel and a whole bunch of others.  Chromium-browser is acceptable but google-chrome is not.  I'm not entirely sure how it decides which one it will drag in if there isn't already one from its list.

---

### Post by Petrolea on 2011-05-19
> **ewaynec said:**
> I don't know.

Try uninstalling via terminal and before continuing it will list the packages that it will remove.

---

### Post by ewaynec on 2011-05-19
I said "I don't know" because it is a moot point, I am not going to re-install Mediatomb, and then un-install it just to see if Chrome is also un- installed, which will prove nothing either way. 
  I will say it one more time, "please read my original post", you are attributing problems to me that I don't have.
  I did not think this would last 30 min. before someone gave me a good solution. I now think no one ever will. How do I mark this thread un-solvable?

---

### Post by uRock on 2011-05-19
> **ewaynec said:**
> I said "I don't know" because it is a moot point, I am not going to re-install Mediatomb, and then un-install it just to see if Chrome is also un- installed, which will prove nothing either way. 

I did not ask you to reinstall it, then remove it. I asked you if removing Chrome after installing Mediatomb would cause the package manager to uninstall Mediatomb. **We are only asking you to uninstall Chrome after installing MediaTomb.**

If we can't recreate your situation, then all we can do is help you work around it.

I see no reason for hostilities. Folks here are only trying to help you.

---

### Post by wolfen69 on 2011-05-19
> **ewaynec said:**
> I may have mis-spoke about Lucid coming with Chrome, but the first thing I do with a new install is download the updates, and there it is.

Something is fishy right there. You should not be getting Chrome just by doing updates. I would check your repos.

---

### Post by mc4man on 2011-05-19
> **ewaynec said:**
> . Every time I get updates it has Chrome included. I un-check it (telling it not to install). It installs it anyway.  Is there any way to stop this?
If inclined, next time this occurs and if using Update Manager - highlight the 'chrome' update, expand the "Description of update" > changes and either take a screen shot or copy, paste and post "Changes for the versions:" -  whatever is shown
If using the terminal to update then copy and paste the complete output

---

### Post by michaelzap on 2011-05-19
> **mc4man said:**
> If inclined, next time this occurs and if using Update Manager - highlight the 'chrome' update, expand the "Description of update" > changes and either take a screen shot or copy, paste and post "Changes for the versions:" -  whatever is shown
If using the terminal to update then copy and paste the complete output

Well, let's be clear here: If the update manager is offering you updates of Chrome, then Chrome is installed on your system. It is not installing Chrome, it is updating it. You apparently have not uninstalled Chrome, and declining an update will not uninstall it.

Open a terminal window and run the following command:
```
sudo apt-get remove google-chrome
```

And then for good measure, also run this one:
```
sudo apt-get remove chromium-browser
```

Once you have actually uninstalled Chrome, you will no longer be offered updates for it, and it will not reappear in your system unless you reinstall it.

---

### Post by tgm4883 on 2011-05-20
> **ewaynec said:**
> I said "I don't know" because it is a moot point, I am not going to re-install Mediatomb, and then un-install it just to see if Chrome is also un- installed, which will prove nothing either way. 
  I will say it one more time, "please read my original post", you are attributing problems to me that I don't have.
  I did not think this would last 30 min. before someone gave me a good solution. I now think no one ever will. How do I mark this thread un-solvable?

I will say this one time. You are hostile and uncooperative. You cannot get help here because what you are saying is impossible. You won't answer any questions that are asked of you, which makes it impossible to help as you have given us a half-baked post which makes not sense.

If you don't get anything else from this thread, understand this one thing.
_There is **NOTHING** in the official repository that will install Google Chrome._ Google Chrome isn't in the official repository, so it is impossible for anything to depend on it for it's installation. If you had the slightest idea of how packaging works you would understand how anything in the official repos depending on Google Chrome is impossible.

So that leaves the other scenario. You or someone with access to your computer installed Google Chrome.

---

### Post by ewaynec on 2011-05-20
I was the one that started this thread, asking for help. Now it is turned into an attack on me because I won't perform like a puppet. I know enough about Ubuntu to know that some of the things you are saying is bogus. You ask me to answer things that I said in the first post. ie "what version are you using?"
  I do not care to carry on this thread, it is going nowhere. I tried everything I could. 
  If you don't know, just say "I don't know".

---

### Post by uRock on 2011-05-20
> **ewaynec said:**
> I was the one that started this thread, asking for help. Now it is turned into an attack on me because I won't perform like a puppet. I know enough about Ubuntu to know that some of the things you are saying is bogus. You ask me to answer things that I said in the first post. ie "what version are you using?"
  I do not care to carry on this thread, it is going nowhere. I tried everything I could. 
  If you don't know, just say "I don't know".

If you uninstalled Chrome, then the package manager would have removed the Google Chrome PPA from your sources list and you wouldn't be offered updates for Chrome when installing softwares via Synaptic. You haven't made it clear whether you actually uninstalled Chrome or if you have just been blocking it from updating and you have said that you will not remove the Google PPA, which serves no purpose without Chrome being installed.

Edit: I have remove all off topic/unhelpful posts, again.

---

### Post by tgm4883 on 2011-05-20
> **ewaynec said:**
> I was the one that started this thread, asking for help. Now it is turned into an attack on me because I won't perform like a puppet. I know enough about Ubuntu to know that some of the things you are saying is bogus. You ask me to answer things that I said in the first post. ie "what version are you using?"
  I do not care to carry on this thread, it is going nowhere. I tried everything I could. 
  If you don't know, just say "I don't know".

I don't want you to perform like a puppet, but you must admit it would be pretty difficult for anyone to help you without the proper information. Please answer the following questions.

[LIST=1]
[*]Please show me the information I have posted that you "know to be bogus"
[*]Can you please post the output of the following two commands?
```
cat /etc/apt/sources.list
```
```
ls -l /etc/apt/sources.list.d/
```
[/LIST]

---

### Post by Elfy on 2011-05-20
Closed for staff review.

---

