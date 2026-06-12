---
title: "extract emails from excel document &amp; newsletter editor"
date: 2010-11-23
forum: General Help
---

### Post by skor78 on 2010-11-23
hi all,

first i'm sorry if this post is in the wrong section, if so, please move it to the right one..

I'm looking for a way to extract 80.000 emails i have in a excel datasheet into a either .txt file or a mailing list file..

Also i'm looking for a good way to send emails, avoiding the use of my email server..

In windows i was use a newsletter editor to do this, but i can't seem to find anything for both this issues for ubuntu, all googles re-direct me to windows software... :x

can u guys help?

Thanx!

---

### Post by SeijiSensei on 2010-11-23
Have you mailed to this list before?  How do you handle bounces?  How do avoid being marked as a spammer?  

If this is a business I suggest you spend a few bucks and try something like [ConstantContact]("http://www.constantcontact.com/").  You can upload your spreadsheet to it and manage all your addresses there.  Their servers will be accepted by everyone, and they'll handle all the bounces automatically.  Their prices are quite reasonable as well.

The answer to your original question is to open the spreadsheet in Excel and save the data back out in something like CSV or tab-delimited formats.  Obviously if you have just a column of email addresses, you'll only get one column of data so tab-delimited is probably the best choice in that case.

---

### Post by skor78 on 2010-11-23
> **SeijiSensei said:**
> Have you mailed to this list before?  How do you handle bounces?  How do avoid being marked as a spammer?  

If this is a business I suggest you spend a few bucks and try something like [ConstantContact]("http://www.constantcontact.com/").  You can upload your spreadsheet to it and manage all your addresses there.  Their servers will be accepted by everyone, and they'll handle all the bounces automatically.  Their prices are quite reasonable as well.

The answer to your original question is to open the spreadsheet in Excel and save the data back out in something like CSV or tab-delimited formats.  Obviously if you have just a column of email addresses, you'll only get one column of data so tab-delimited is probably the best choice in that case.

Thanx 4 u'r answer Seiji,

No, it's a brand new database, i bought. 
ConstantContact as well as others similar services ask for around 250€/month for 100.000 contacts, but i just want to do this one single time, it's one single advertising email with products dedicated for companies only. that's why i'm looking for a third party solution.. also i do not like the idea of providing my mailing list of companies (which i payed for) to another company..

The data sheet has several columns with name, sector, address, phone, mobile, website, email, etc.., and what i want to do is to extract only the emails, then i could (in ex., in case i can't get a soft to do this for me) divide them in several files and use them to do the mass email sending, avoiding being blocked/crashed by the mail servers.

If you could help with such extraction, it would be great!

Thanx!

---

### Post by SeijiSensei on 2010-11-23
1)  Create a new empty sheet in Excel and copy the entire column of email addresses into its first column.  If you're handy with Excel, first create a column in the original datasheet that consists of just the domain part of each address using a formula that splits the address on "@".  There's a function for this, but I don't remember it off the top of my head.  Then sort the data by domain so all the "aol.com" addresses are together, etc.  Now copy the column of sorted emails into the new sheet.

2)  Save the new sheet as a tab-delimited file (see the Save As options).  You'll get a plain-text version of the file.  I believe you can save it in "Unix" format to get rid of the DOS CRLF end of line problem.  Otherwise install the "tofrodos" package and use the "fromdos" command  to strip the line feeds.

3)  I'd probably split the list into blocks of 5-8,000 for manageability.  Now create an alias in sendmail or Postfix that points to the list (or one of the sublists if appropriate).  In sendmail it would be stored in /etc/aliases and look like:

friends:    :include:/path/to/the/list

Run the "newaliases" command as root when you're done.  If you're using Postfix, you'll need to read the documentation.

4) Send the message to the alias, e.g, "friends@example.com".  Wait for the deluge of bounces and out-of-office replies to overwhelm your inbox, then point the alias to the next list file and repeat.  You might want to create a separate email account to use as the sender so all the replies come to that mailbox.  Creating a couple of mail filters for the account to handle bounce notices and out-of-office replies will probably make your life easier.

Do not put the addresses in either a To or a CC field; every recipient will be able to see the entire list if you do that.  You could send a message to yourself or some other address with the list in a Bcc, but I think a generic alias works better.

The other alternative would require writing a custom script in bash or something like PHP or Python that would iterate over the list and send a separate message to each recipient.  So instead of my getting an email to "friends@example.com" I'd get one addressed to "seijisensei@somewhere.net".

---

### Post by skor78 on 2010-11-24
Hi SeijiSensei,

Just wanted to say thanx alot for the great tip. I was already able to create a mailing list in text format, with a email in each line, however, i couldn't add the ';' after the e-mail to make it perfect, but for this i'm going to use wpa wordlist optimizer from aircrack tools that allows me to add a specific char to each word.. :D Before this i'd never think aircrack tools could be applicable in so many different ways.. ;)

About your e-mail sending script, i must confess i need to do a little more reading, as i'm still too green under linux, but i hope by tomorrow i'll have some more on that, if not already completed..

But i'd still like to try it in another way, maybe you can help understanding how this works, or how i can create a script similar to the app i'll explain next..

Under Windows i was using a trial ver. of **Effective Newsletter Studio**, and with this app what happened was, i only needed to write whatever mail i wished to be sender, without any mail server configurations, or filtering at all.. After this i selected my mailing list and send. I've tested the program, and it worked!! even as a joke, i've written the recipient was 'support@microsoft.com' and send the newsletter to my email, and it was there, from 'support@microsoft.com'!! :D Unfortunately the trial ver. is limited to sending 100 emails, and the full version costs 650€.. :-&

Obviously, my question is, can a similar sending script be created under ubuntu? 
If so, i wouldn't need to worry with bounces and out-of-office replies, i'd just use a inexistent e-mail address, in ex. 'no-reply@something.com'

Once again, thanx for all your help!

Cheers!

---

