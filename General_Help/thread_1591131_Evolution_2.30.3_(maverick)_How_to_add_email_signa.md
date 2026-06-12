---
title: "Evolution 2.30.3 (maverick) How to add email signature?"
date: 2010-10-08
forum: General Help
---

### Post by foxmulder881 on 2010-10-08
Am I stupid or something? I just upgraded to Maverick yesterday. When I used to compose a new email I was able to add my email signature to it via a little drop down menu in the compose window. Where has it gone? I can't see any way at all to add my signature to my emails. :confused:

---

### Post by drs305 on 2010-10-08
[Edit: The OP was happy to have a default sig automatically added. 
For those who want to have a drop down for multiple signature options but can't get one: If you have only one email account, see Post 23 for solution. ]



I have the ability to set the sig via Edit, Preferences: Composer Preferences, Signature Tab. Create and save the sig.

When I compose a new email, there is a box to the top far right which allows me to select the signature. I'm using 2.30.3, 64-bit Maverick.

---

### Post by foxmulder881 on 2010-10-08
> **drs305 said:**
> When I compose a new email, there is a box to the top far right which allows me to select the signature. I'm using 2.30.3, 64-bit Maverick.

Not on mine. Screenshot below.

[[IMG]http://img69.imageshack.us/img69/4250/201010091046441680x1050.th.png[/IMG]](http://img69.imageshack.us/i/201010091046441680x1050.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by drs305 on 2010-10-08
I can't make out the graphic but I trust your eyes. 

I've played around with formats, how to generate the message, etc, and I *can't* find a way to get the signature drop box to disappear. Sorry.

---

### Post by foxmulder881 on 2010-10-08
> **drs305 said:**
> I can't make out the graphic but I trust your eyes. 

I've played around with formats, how to generate the message, etc, and I *can't* find a way to get the signature drop box to disappear. Sorry.

WHAT! Just click on the image to make it full size. 1680 x 1050. If you can't see it at that resolution I think you may need to get your eyes checked. :P No offense intended.

This is really annoying considering this is my work email also.

---

### Post by drs305 on 2010-10-08
Fired up the 32-bit laptop and it showed there too.

But I figured it out. Now I have to decide if I'll tell you since you cast aspersions about my eyesight.



Oh alright! After all - it *is* Ubuntu....

I have to have the "From:" field enabled at the top. When I remove the "From" field, it takes the "Signature" button with it since they are on the same line.  ](*,)

---

### Post by foxmulder881 on 2010-10-08
> **drs305 said:**
> Fired up the 32-bit laptop and it showed there too.

But I figured it out. Now I have to decide if I'll tell you since you cast aspersions about my eyesight.



Oh alright! After all - it *is* Ubuntu....

I have to have the "From:" field enabled at the top. When I remove the "From" field, it takes the "Signature" button with it since they are on the same line.  ](*,)

Ok, I accept that was probably a low-blow. lol. But considering you are going to help me, I take it back. But I have to admit I was little shocked that you seriously could not see it.


And how do I get the "From" field to appear when I only have one email account setup?

---

### Post by drs305 on 2010-10-08
On my 64-bit machine, in the message window I can't get rid of the "From:" field via View. There are no options for "From". I guess I am just lucky it defaulted to showing. I can't find a setting to change it.

In my 32-bit Evolution, the message window has the "From" option box via the View menu, so it's easy to turn on/off.

I'll keep playing with it to see if I can find a rationale or solution.

By the way, I right click the image and it says it's 150x94 pixels.

---

### Post by drs305 on 2010-10-08
```

gconftool-2 --set --type bool /apps/evolution/mail/composer/show_mail_from true

```

This turns on the "from" field for me on the Evolution that doesn't have the 'frozen ON' "From" field.

---

### Post by foxmulder881 on 2010-10-08
Well how the hell does that make sense that the 32 bit Evolution and 64 bit version get 2 different options?

---

### Post by foxmulder881 on 2010-10-08
> **drs305 said:**
> ```

gconftool-2 --set --type bool /apps/evolution/mail/composer/show_mail_from true

```

This turns on the "from" field for me on the Evolution that doesn't have the 'frozen ON' "From" field.

Doesn't change anything on mine. :-(

---

### Post by foxmulder881 on 2010-10-08
Just performing a dist-upgrade now. There's quite a few packages that require updating, so I'll see if that changes anything.

---

### Post by drs305 on 2010-10-08
> **foxmulder881 said:**
> Just performing a dist-upgrade now. There's quite a few packages that require updating, so I'll see if that changes anything.

I've been downloading the updates in my Maverick VM. It's been a long time since I've used it so there are lots of updates. Thought I could take a look at a clean install of Evolution to see what it's doing.

---

### Post by foxmulder881 on 2010-10-09
Nothing has changed after updating to the latest packages.

Should I be reporting this as a bug or not?

---

### Post by plucky on 2010-10-09
How many email accounts do you have enabled?

When I disable all my email accounts (Edit > Preferences > Mail Accounts) then the "From" box doesn't appear.It also doesn't appear if you only have one email account enabled,which is the bug I think as the signature box also disappears.

This is on a 64-bit Maverick in Virtualbox.

Good Luck

---

### Post by drs305 on 2010-10-09
> **foxmulder881 said:**
> Nothing has changed after updating to the latest packages.

Should I be reporting this as a bug or not?

Definitely a bug if you can't get the signature button with only one account.  

```
ubuntu-bug evolution
```

---

### Post by drs305 on 2010-10-09
No solutions but I think I may have found out part of the problem. As I mentioned previously one of my two systems has the "From" field permanently on and I can't change it. Fortunately that also keeps the 'signature' box on display.

On the frozen system, I looked a little harder at the gconf-editor settings. I couldn't understand why the '/apps/evolution/mail/composer/show_post_from' would not work.

Finally, I saw the description: 
> Show "From" field when [COLOR="Red"]posting to a newsgroup[/COLOR]'.
Long Description: Show "From" field when [COLOR="Red"]posting to a newsgroup[/COLOR]'. This is controlled from the View menu when a news account is chosen.


In previous versions, the description, which makes more sense, is:
> Show "From" field when[COLOR="Red"] sending a mail message[/COLOR]'.

So it appears at least from the description that the "From" field (and signature button) are now intentionally or unintentionally tied to newsgroups.  ](*,)

---

### Post by dcstar on 2010-10-09
> **drs305 said:**
> Definitely a bug if you can't get the signature button with only one account.  


Yep, confirmed it on my 10.10 64-bit test system - multiple accounts ok, single account no Signature selection box (along with the "From" selection).

---

### Post by bob brazie on 2010-10-10
Show "From" field when posting to a newsgroup'.
Long Description: Show "From" field when posting to a newsgroup'. This is controlled from the View menu when a news account is chosen. 

Where can I find this newsgroup item? I can't even find newsgroupes in Evolution. <g>

Thanks in advance. Bob.

---

### Post by drs305 on 2010-10-10
> **bob brazie said:**
> Show "From" field when posting to a newsgroup'.
Long Description: Show "From" field when posting to a newsgroup'. This is controlled from the View menu when a news account is chosen. 

Where can I find this newsgroup item? I can't even find newsgroupes in Evolution. <g>

Thanks in advance. Bob.

I spent about 10 minutes trying to find out how to do this but there isn't a lot of information about it. I know you select "USENET NEWS" on the Server setup page while making a new account but not a lot more about it.

Unless the OP wants to discuss it I would suggest you start a new thread - which in light of the scarcity of info on this topic might not be a bad idea.

---

### Post by foxmulder881 on 2010-10-12
> **plucky said:**
> How many email accounts do you have enabled? <snip>

Only use one email account these days. Both for work and personal.

Apart from this niggle, I'm very happy with Maverick. But I sure do miss my email signature. :(

---

### Post by lviggiani on 2010-10-12
Hi guys,
same problem here on Maverick 64bit (upgraded from Lucid). No button for adding email signature... very annoying.
I've been reading the thread but I'm still confused... is that actually a bug? Has some one found a temp workaround?
Thanks, Luca.

---

### Post by drs305 on 2010-10-12
> **lviggiani said:**
> Has some one found a temp workaround?
Thanks, Luca.

I'm not really affected by this since I have multiple accounts, but I came up with a workaround if you only have one account.

I'd backup your current settings before messing with this, both via the built-in backup (File, Backup Settings) and running the command. I'm just paranoid, enhanced by my willingness to break things for coming up with forum solutions. ;-)
```
cp -R ~/.evolution ~/.evolution.bak && cp -R ~/.camel_certs ~/.camel.certs_bak
```

Create a second account: Edit, Preferences, Mail Accounts > Add.
Use an email address of "none@none".

Receiving Email: 
Server Type: None

Sending Email: 
Server Type: SMTP
Server: "none" 
Server Req Auth ticked, but leave authentication empty.

Notes:
By selecting 'None' on the receiving email server it won't try to connect.
By selecting Authentication but leaving the password blank I figure I'd be prompted if something actually tried to use the account.

As far as I can tell, creating a second account in this manner will be completely transparent and you won't even know it exists, except that you will have your 'signature' button.

---

### Post by lviggiani on 2010-10-12
> **drs305 said:**
> I'm not really affected by this since I have multiple accounts, but I came up with a workaround if you only have one account.

I'd backup your current settings before messing with this, both via the built-in backup (File, Backup Settings) and running the command. I'm just paranoid, enhanced by my willingness to break things for coming up with forum solutions. ;-)
```
cp -R ~/.evolution ~/.evolution.bak && cp -R ~/.camel_certs ~/.camel.certs_bak
```

Create a second account: Edit, Preferences, Mail Accounts > Add.
Use an email address of "none@none".

Receiving Email: 
Server Type: None

Sending Email: 
Server Type: SMTP
Server: "none" 
Server Req Auth ticked, but leave authentication empty.

Notes:
By selecting 'None' on the receiving email server it won't try to connect.
By selecting Authentication but leaving the password blank I figure I'd be prompted if something actually tried to use the account.

As far as I can tell, creating a second account in this manner will be completely transparent and you won't even know it exists, except that you will have your 'signature' button.

Hi, I followed your instructions and I have my magic button back again!
Thank you very much!
BTW, has someone already submitted a bug?
I have also noticed that when a new message arrives it is marked in bold (and this is ok). Anyway is stays bold even after it has been read (open) unless I click on its "envelope" icon from the message list. Anyone else notice that?

---

### Post by bob brazie on 2010-10-12
Yes, I have reported it at the Launchpad site and have heard nothing back yet that it is even a bug.

Bob.

---

### Post by foxmulder881 on 2010-10-14
I would consider this issue quite severe. Especially in my case from a business perspective, yet not much attention has been associated with it so far.

---

### Post by dcstar on 2010-10-14
> **foxmulder881 said:**
> Only use one email account these days. Both for work and personal.

Apart from this niggle, I'm very happy with Maverick. But I sure do miss my email signature. :(

E-mail signatures can be added **automatically** to new messages, this bug is about the **manual** selection of different signatures.

---

### Post by bob brazie on 2010-10-14
That and the fact that now weekends can't be un-compressed either.

Why do newer versions always seem broken?

Bob.

---

### Post by foxmulder881 on 2010-10-14
> **dcstar said:**
> E-mail signatures can be added **automatically** to new messages, this bug is about the **manual** selection of different signatures.

Oh my god, this is what I've been ranting about the whole time. I thought there was no ability to add ANY signature unless there was multiple email accounts. I feel like such a **** now.

Why did no one tell me this!

> **bob brazie said:**
> Why do newer versions always seem broken?

Bob.

Generally speaking, I find they're not.

---

### Post by drs305 on 2010-10-14
> **foxmulder881 said:**
> Oh my god, this is what I've been ranting about the whole time. I thought there was no ability to add ANY signature unless there was multiple email accounts. I feel like such a **** now.

Hehe! And all this time I thought you were looking at ways to put in one of a *collection* of signatures (one for business, one for home). 

So that makes two of us!  ](*,)

---

### Post by foxmulder881 on 2010-10-14
> **drs305 said:**
> Hehe! And all this time I thought you were looking at ways to put in one of a *collection* of signatures (one for business, one for home). 

So that makes two of us!  ](*,)

Nup. Only one sig for one email. It's okay, I've done it now. G#! D&$%! ](*,) <repeats>

---

### Post by LucidForm on 2010-10-14
Try going to: Edit Menu -> Preferences -> Mail Accounts Section -> Edit Button.
There's a "Signature" dropdown box in the Identity tab which lets you select a default signature for that account.

I'm running Maverick and Evolution 2.30.3.

Hope this helps!

---

### Post by chuckh1958 on 2010-10-21
> **drs305 said:**
> ```

gconftool-2 --set --type bool /apps/evolution/mail/composer/show_mail_from true

```

This turns on the "from" field for me on the Evolution that doesn't have the 'frozen ON' "From" field.

I'm having the same problem - no signature dropdown - after upgrading to maverick. I tried the above workaround to enable the "from" field but it still does not appear in the view menu on the message composer.

---

### Post by drs305 on 2010-10-21
> **chuckh1958 said:**
> I'm having the same problem - no signature dropdown - after upgrading to maverick. I tried the above workaround to enable the "from" field but it still does not appear in the view menu on the message composer.

Do you have only one email account? As this thread progressed we discovered that with only one email account you aren't going to get the signature dropdown box (you *can* have an automated signature, just not a chance to pick from a selection). 

To get the drop down menu you have to have 2. I detailed how to create a dummy account in post # 23.

---

### Post by chuckh1958 on 2010-10-21
Well if adding a 2nd email account fixes it I can manage that. I'll give it a try.

---

### Post by RunningUtes on 2010-10-24
Worked for me. Here is the link to my AskUbuntu post on the issue.
[http://askubuntu.com/questions/9156/how-can-i-attach-different-signatures-to-individual-emails-using-the-same-account]("http://askubuntu.com/questions/9156/how-can-i-attach-different-signatures-to-individual-emails-using-the-same-account")

---

### Post by enid on 2011-03-07
> **drs305 said:**
> I'm not really affected by this since I have multiple accounts, but I came up with a workaround if you only have one account.

I'd backup your current settings before messing with this, both via the built-in backup (File, Backup Settings) and running the command. I'm just paranoid, enhanced by my willingness to break things for coming up with forum solutions. ;-)
```
cp -R ~/.evolution ~/.evolution.bak && cp -R ~/.camel_certs ~/.camel.certs_bak
```Create a second account: Edit, Preferences, Mail Accounts > Add.
Use an email address of "none@none".

Receiving Email: 
Server Type: None

Sending Email: 
Server Type: SMTP
Server: "none" 
Server Req Auth ticked, but leave authentication empty.

Notes:
By selecting 'None' on the receiving email server it won't try to connect.
By selecting Authentication but leaving the password blank I figure I'd be prompted if something actually tried to use the account.

As far as I can tell, creating a second account in this manner will be completely transparent and you won't even know it exists, except that you will have your 'signature' button.
Hi, 
I have the same issue here on Evo 2.30.3 and the only workaround that worked for me was this above.
Thanks :)

---

