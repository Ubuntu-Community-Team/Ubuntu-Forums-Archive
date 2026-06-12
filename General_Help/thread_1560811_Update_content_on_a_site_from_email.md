---
title: "Update content on a site from email"
date: 2010-08-25
forum: General Help
---

### Post by karmic-koala on 2010-08-25
Hi all,

Is there a way you could update content on a web page from an incoming email on a linux server?

e.g. you email your comments to an email address and the contents of your email (comments) appear on a web page.

(preferably in real time but some delay acceptable)

---

### Post by quizno50 on 2010-08-25
I would look into a blogging software like wordpress or something like that. I do all my web programming myself, so I can't say which would have that, but if you have some basic programming knowledge it shouldn't be to difficult to code up in PHP.

---

### Post by sydbat on 2010-08-25
> **karmic-koala said:**
> Hi all,

Is there a way you could update content on a web page from an incoming email on a linux server?

e.g. you email your comments to an email address and the contents of your email (comments) appear on a web page.

(preferably in real time but some delay acceptable)As far as I know - no. As quizno50 suggests, using something like Wordpress would allow you to simply log in from anywhere in the world and create new content.

---

### Post by karmic-koala on 2010-08-25
The actual application itself is no problem. I could program that if there were some way to connect to an smtp host and grab emails (e.g. as files) in real time.

---

### Post by TNT1 on 2010-08-25
> **sydbat said:**
> As far as I know - no. As quizno50 suggests, using something like Wordpress would allow you to simply log in from anywhere in the world and create new content.  Yip. I have a wp site of my own, it's dead easy - in contrast to my other sites running ruby on rails... I suck at being a geek.

---

### Post by karmic-koala on 2010-08-25
But I am not thinking on the lines of blogging, what I had in mind was an issue tracking system such that people could mail issues and those issues appear as a list on an authenticated page.

---

### Post by TNT1 on 2010-08-25
Oh, right, a quick scroogle says that there are several ways.  [http://extensions.joomla.org/extensions/news-production/microblogging/12215](http://extensions.joomla.org/extensions/news-production/microblogging/12215) [http://foundbydesign.com/seo/site-to-social-auto-add-articles-to-twitter/](http://foundbydesign.com/seo/site-to-social-auto-add-articles-to-twitter/) [http://www.forumpostrobot.com/](http://www.forumpostrobot.com/) [http://codex.wordpress.org/Post_to_your_blog_using_email](http://codex.wordpress.org/Post_to_your_blog_using_email)  I'd use the codex or joomla ways, like I said, I suck at geek...

---

### Post by karmic-koala on 2010-08-25
> **TNT1 said:**
> [http://codex.wordpress.org/Post_to_your_blog_using_email](http://codex.wordpress.org/Post_to_your_blog_using_email)

Thanks for that link its spot on, only it works with wordpress and the issue report system is something i will develop from a scratch.

---

### Post by TNT1 on 2010-08-25
> **karmic-koala said:**
>  the issue report system is something i will develop from a scratch.  Using?

---

### Post by karmic-koala on 2010-08-25
> **TNT1 said:**
> Using?
Django and Python

---

### Post by TNT1 on 2010-08-25
> **karmic-koala said:**
> Django and Python  Sorry, I can do RoR, not python. Try reverse the joomla plugin for what you want to do?

---

### Post by keithpeter on 2010-08-25
Hello Karmic-Koala

[http://stackoverflow.com/questions/730573/django-to-send-and-receive-email](http://stackoverflow.com/questions/730573/django-to-send-and-receive-email)

Would it be better to ask on django/python forums? Once you have your platform running, the OS matters little except for knowing how e-mail gets routed?

---

### Post by karmic-koala on 2010-08-25
Found something that may help folks with similar set of requirements - imaplib for python - its able to connect to Gmail and fetch messages etc, although this requires knowledge of IMAP Protocol to fetch relevant/required content.

---

