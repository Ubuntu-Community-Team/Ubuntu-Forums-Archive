---
title: "Tweetdeck can't access passwords after upgrade to Ubuntu 1110"
date: 2011-10-14
forum: General Help
---

### Post by jonbjoseph on 2011-10-14
I just upgraded from Ubuntu 1104 to 1110.  When I startup Tweetdeck , I get the following message:

Tweetdeck is having trouble using some of your passwords that are stored securely on your machine. Clicking submit will clear this data so that you continue to use Tweetdeck.  

There is only an ok button (no submit button). After clicking the ok button in the message, Tweetdeck displays a blank area, where the tweets are normally displayed.

What can be done to try and fix this problem?  Is this a permissions issue on a file or files that store my passwords?  

Thanks,
Jonathan

---

### Post by jonbjoseph on 2011-10-15
I've tried the suggestions at: [http://kb2.adobe.com/cps/492/cpsid_49267.html](http://kb2.adobe.com/cps/492/cpsid_49267.html)

$ mv ~/.gnome2/keyrings/ ~/.gnome2/keyrings.bkp
$ mkdir -p ~/.gnome2/keyrings/
rm -rf ~/.appdata/Adobe/AIR/ELS

I got prompted for a username and password 2 times as follows:
New Keyring Password
An application want to create a new keyring called 'Default'. Choose the password you want to use.

Then I get the same error message as before:
Oops, TweetDeck can't find your data
Tweetdeck is having trouble using some of your passwords that are stored securely on your machine

So no luck in fixing this problem thus far.
Jonathan

---

### Post by jonbjoseph on 2011-10-16
I still have the have the problem after removing and reinstalling TweetDeck.

After the TweetDeck installation, TweetDeck starts up and I get the message:
Enter the password to unlock your login keyring.
The login keyring didn't get unlocked when you logged into your computer.

---

