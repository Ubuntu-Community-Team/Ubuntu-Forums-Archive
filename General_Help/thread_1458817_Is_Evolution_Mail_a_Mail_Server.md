---
title: "Is Evolution Mail a Mail Server?"
date: 2010-04-20
forum: General Help
---

### Post by ajwei810192 on 2010-04-20
Hi, 

I have recently installed a lamp server using Ubuntu, and I am trying to set up a contact page using PHP and PEAR, and have the mail delivered to my mailbox. I have set up the mailbox using Evolution Mail, but I have not touched the php.ini file yet. 

I get this message saying that my message has been sent, but I never see the email. I posted this to the PHP forums a couple of times, and no one seem to be able to answer the question. Here is the code:


if($_POST['submit']=="Submit") {
$from  = "localhost";
$to =  $email;
$subject = "Comments";
$body = "From: $your_name\n E-Mail: $email\n  Reason Contact: $question\n Comments:\n $comments";

$headers = array ('From' => $from,'To'  => $to,'Subject' => $subject);
$mail ->send($to, $headers,  $body);

Is Evolution a Mail server that I can use to send mail? 
Thanks for your help.

Alice

---

### Post by huwnet on 2010-04-20
No, Evolution is a mail client that you use to receive and compose e-mail.

You'll need to look at Postfix, Sendmail or exim. These are all different available mail servers which should have documentation available on the Ubuntu wiki.

If you're hosting this on your home PC, you'll probably need to configure the mail server to forward e-mail from the mailserver to your ISP's mailserver before being sent out onto the web.
Alternatively, if you already have webhosting your provider should already have a working mailserver for you to use.

You could also look at saving contact messages to a file instead of e-mailing them to yourself :)

---

### Post by dcstar on 2010-04-21
> **huwnet said:**
> No, Evolution is a mail client that you use to receive and compose e-mail.

You'll need to look at Postfix, Sendmail or exim. These are all different available mail servers which should have documentation available on the Ubuntu wiki.

If you're hosting this on your home PC, you'll probably need to configure the mail server to forward e-mail from the mailserver to your ISP's mailserver before being sent out onto the web.


There is no need to use an external SMTP server if you have a MTA set up on your own PC - **except** if you have a dynamic IP address than may have been identified as a Spam source, or e-mail destinations you send to reject mail from your IP address because it is not associated with a DNS entry.

---

### Post by ajwei810192 on 2010-04-21
dcstar and huwnet, 
 
I found out that I have missing packages from my linux box that cause my PHP not be able to work the way I wanted, which includes not able to use the sendmail or mail function. 

 As the time of writing this, I have installed the missing Net_SMTP pear package unto my Linux box. I have just tested it, and I have received two email messages to the desired mailbox, without having to install a mail server.

I really appreciate this.

---

### Post by Sweaty on 2011-06-24
I just dont want to rely on google search alone for setting up an email server for my house.please can someone give me good options.

Thanks

---

### Post by mamta on 2011-07-04
Try this .[http://bestemailservers.info/.](http://bestemailservers.info/.)Hope it helps you.

---

### Post by Sweaty on 2011-08-16
I
think QUESTION 
POSTER'S NAME mamta 
has some experience of good server providers. URL [http://bestemailservers.info/](http://bestemailservers.info/)
surely are good and I have contacted them...

---

