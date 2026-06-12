---
title: "Gmail in text browser"
date: 2009-11-01
forum: General Help
---

### Post by Esthellin on 2009-11-01
I do not want to have a separate email program on the computer to check email, so I am using Firefox to check my Gmail and Hotmail accounts.
But, because I am obsessed with the Terminal, I would like to check email from there.

My web text-browser for the terminal is w3m, which works for most things.

P.S. My gmail account is a Google Apps account, and I have set the default view in Google Apps to be standard HTML

Loading the google apps account however results in the page showing two embedded text boxes, one with a load of gibberish, looks like a certificate. The other has a very long link, with the typed in email address in it.
Loading this in Firefox gives a loading bar, so this is probably why it is stuffing up. But this loading bar shouldn't appear if 'standard HTML' view is chosen.

Any suggestions?

---

### Post by 133794m3r on 2009-11-01
> **Esthellin said:**
> I do not want to have a separate email program on the computer to check email, so I am using Firefox to check my Gmail and Hotmail accounts.
But, because I am obsessed with the Terminal, I would like to check email from there.

My web text-browser for the terminal is w3m, which works for most things.

P.S. My gmail account is a Google Apps account, and I have set the default view in Google Apps to be standard HTML

Loading the google apps account however results in the page showing two embedded text boxes, one with a load of gibberish, looks like a certificate. The other has a very long link, with the typed in email address in it.
Loading this in Firefox gives a loading bar, so this is probably why it is stuffing up. But this loading bar shouldn't appear if 'standard HTML' view is chosen.

Any suggestions?
You are speaking of just the actual page [www.gmail.com](www.gmail.com) correct? When you login it isn't working?

Before i read your post about "w3m" and "terminal based web browsing" i had never heard of either of these things being in ubuntu. 

But i can tell you this much atleast from my end. I'm on ubuntu 9.10 x64. I also have the w3m that comes with it. I tried to get to my gmail account on there so that i could see if it was also present in this release. 

So when i did it, it did work. I had no problems with the 2 text boxes and it loaded just fine. I even have my default as the "terminal theme" that's probably why it works so well in the terminal. :P but in all seriousness. It worked just fine for me, i was able to login after messing around with it a bit to realize what this thing did. I also was able to check some of my messages and logout. The only thing i didn't know how to do was how to find a new page from the browser or open new tabs. But that's b/c i hvae never used it before. 

In summary, when you have the time burn the 9.10 live cd and see if it works there. If it does and your'e willing to go to 9.10 do it. Other than that i have no idea why it's not rendering right for you.

---

### Post by Esthellin on 2009-11-01
I am speaking of loading the google apps page for my university which in this case is mail.google.com/a/student.adelaide.edu.au.
The username and password is typed in, and then it gives those two text boxes.

Is it a problem with redirecting?

w3m is a sweet program, great for checking these forums without seeing everyone's avatars :P

What do you mean by 'terminal theme'?

---

### Post by Jeffonfire on 2009-11-01
I use lynx for command line browsing and that works for me. I know that it does redirect which and this for some reason causes lynx to be slow.

W3m looks like an interesting program, I should try it. Hope that helps a bit.

---

### Post by Esthellin on 2009-11-01
I just installed lynx.

It failed. Miserably.
It said "SSL error: no issuer was found-Continue?"

It had ALOT of trouble jstu accepting the cookie from google.com. It took 5 "Always" before it accepted it, then went "Bad HTML!!" then loaded.

---

### Post by 133794m3r on 2009-11-02
i meant from the theme itself. You know the themes that google has. It was a joke. Since as you may/may not know google's now got themes that you can choose from and i chose that one. Now about the issue with page changing. I didn't know how to go to a new page from the w3m.

And my school doesn't use google apps yet. Which is saddening i know. But me and the entire group of people who took Tech Forsight are trying to get them to.

I have no idea how to help you then as i don't have a google apps page for my school. And logging in with yours would obviously be impossible since i don't go to your school. It seems like someone else who has a google apps account for schools will have to check this one out...

---

### Post by Esthellin on 2009-11-02
While I wait from a Google Apps user to reply, maybe I should try and find an email provider that will have support for text-browsers (eg no Javascript) and forward all emails to that address.

Any suggestions? Hotmail and gmail both need javascript to work, so those arent good.

---

### Post by 133794m3r on 2009-11-02
you don't have javascript installed on your system? O_o

That's probably it then... as i was running it from the terminal but well i do have java installed.

---

### Post by Esthellin on 2009-11-02
With all the text-browsers I know, none of them support Java-script (which sucks majorly). 
That is the reason (I think) that I can't access any of the email accounts. But if I set Google apps to have the plain html view, it should work, but doesn't :(

---

### Post by 133794m3r on 2009-11-02
you have a normal gmail account you can try it from? And well i guess all i can say is... good luck finding an email service that doesn't use java. And hopefully someone soon will come on that has a google apps account.

---

### Post by Esthellin on 2009-11-02
I have just tested that with a normal Gmail account.

A faily simple page loaded saying "The page you requested was invalid".

---

### Post by 133794m3r on 2009-11-02
I'm outta idea then... as it's working for me in Ubuntu 9.10 x64. With the w3m that comes with it. No extra html browsers or any other such things. I'm completely out of ideas and will now be going to eat supper then watch some tv. I hope someone out there can help you with this as i'm outta ideas.

---

### Post by Esthellin on 2009-11-02
Thanks for your help. Maybe I should upgrade to Karmic...but I want to wait until other people have ironed out its bugs.

Patience I must have :P

---

### Post by sisyphus1978 on 2009-11-03
I just checked my googleappsfordomains email and my regular gmail in w3m. Worked okay. I was getting a page invalid link, but I tried a few things (don't ask me what) and it all started working. Think it may have been a cookie thing...

Posting this from w3m 9.10 :)

---

### Post by Esthellin on 2009-11-03
What was your starting link to get the google apps site?
Maybe I am logging in from the wrong starting link.

Please sisyphus1978 try and find out what you changed to get it working.

---

### Post by sisyphus1978 on 2009-11-03
I didn't do anything. I just pointed w3m to the mail page for my googeappsfordomain. It logged in 
fine. Maybe you should talk to your IT guys. My regular gmail was harder to get working. But I 
tried logging into to https and it worked. Maybe your admin has set only https login? I dunno.

---

### Post by gmc on 2009-11-03
Have you considered using Mutt? If you set your gmail account to allow imap access you can use [http://crunchbanglinux.org/wiki/howto/howto_setup_mutt_with_gmail_imap](http://crunchbanglinux.org/wiki/howto/howto_setup_mutt_with_gmail_imap) to configure it to access your email.

Mutt is in the repositories and quite frankly, you'll be hard pressed to find a more powerful email client (though it might give you a few gray hairs too) :-)

G

---

### Post by marshag63 on 2009-11-03
Try elinks text browser. I had no problem accessing my gmail account with it.  Don't forget to set your gmail to use https in gmail's config files :)

Here's a tip:  Press the "period" key to turn on numbered links - press a number, jump to a link.

Use Insert and Delete to scroll up/down as well as page-up/down.

You can have multiple pages (tabs) open - just press "t" for a new tab and type in the URL, "c" to close the tab, "q" to quit elinks, and <> to move through your tabs.

MarshaG

---

### Post by andrew.46 on 2009-11-03
Hi gmc,

> **gmc said:**
> Have you considered using Mutt? If you set your gmail account to allow imap access you can use [http://crunchbanglinux.org/wiki/howto/howto_setup_mutt_with_gmail_imap](http://crunchbanglinux.org/wiki/howto/howto_setup_mutt_with_gmail_imap) to configure it to access your email.

The more old-fashioned way of doing this, i.e. without imap, can be seen here:

[Howto] Use Mutt with Gmail
[http://ubuntuforums.org/showthread.php?t=1021746](http://ubuntuforums.org/showthread.php?t=1021746)

Andrew

---

### Post by Esthellin on 2009-11-03
> **sisyphus1978 said:**
> I didn't do anything. I just pointed w3m to the mail page for my googeappsfordomain. It logged in 
fine. Maybe you should talk to your IT guys. My regular gmail was harder to get working. But I 
tried logging into to https and it worked. Maybe your admin has set only https login? I dunno.

That is highly possible. Stupid IT guys :P.


I haven't had any luck getting Mutt to work.

---

### Post by Esthellin on 2010-07-03
I have had no luck still with getting access to my googleapps email from w3m. I am now using 9.10 (32 bit) but I still won't get past the 2 boxes. Probably that redirection stuff.

I did another check with my regular gmail account in the new version of w3m. Still no dice. It keeps coming up with "The requested page is invalid." I set in the gmail settings for ito use https always, and for the interface to be basic HTML.

Anyone else tried this with the 9.10 32 bit version using w3m accessing normal gmail accounts?

---

