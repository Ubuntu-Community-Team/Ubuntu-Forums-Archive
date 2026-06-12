---
title: "How do I write a web crawler which applies for jobs?"
date: 2012-07-04
forum: General Help
---

### Post by jon80 on 2012-07-04
I am planning/thinking, of writing a program, which revolves around a personalized concept that I call "web spider".  

A web spider is defined as is a computer program that browses the World Wide Web in a methodical, automated manner or in an orderly fashion, and, carries out clicks on buttons, in a scripted manner.

The term is borrowed from the term web crawler which is defined at [http://en.wikipedia.org/wiki/Web_crawler](http://en.wikipedia.org/wiki/Web_crawler).

The webspider reads buttons off my Gmail account, whilst the OS user is logged on, and browsing the web - whether the user session is visible or not to the user within the UI - and clicks buttons such as those titled 'Apply Now' received from recruitment agencies, and, automatically launches a wizard which:

It may be the case that the user might wish not to apply, in this case no action is taken by the web spider because all the user needs to do is read his her email.  Perhaps sending him/her a reminder about it automatically, is an optional option that would be available within the web spider.

1a) optionally searches the job description for keywords inputted against a given set, logging every entry read in detail on the web server logs during the learning phase of the web spider application.

1b) either clicks the 'apply' button, by parsing the page source (HTML/PHP/JavaScript) of the webpage and learns a process for applying on behalf of the user, taking, for example the resume which is stored on the user's computer, or, on some drive on the cloud, and, using the information within the resume to intelligently filling the standards web forms.  

If intelligence is not possible at first, I would be happy if I had a model for devising a script which at least allows me to write stuff to an HTML form.  

Perhaps some web load testing tool such as WebLoad ([http://www.radview.com](http://www.radview.com)) might help me script something up, however I only had a cursory view of the tool so far, so I am open to suggestions for alternatives.

The web spider submits the job application form, and, now the recruiters are aware of my job application.

When I receive an email from recruiters, I want to parse the email text and use text-based rules so that, I may for example, send a polite reply upon unsuccessful applications, reading:

Whilst thanking you for your reply, it would be appreciated if you kindly provide further feedback on the compatibility of the resume to your requirements?

Regards,


John Doe
[http://linkedin.profile](http://linkedin.profile)

This is because I have noticed that recruiters are frequently high on adrenalin, and, seem to send polite emails only after having had a cursory review of job applications, given the speed and heftiness of their replies.  Sometimes they withhold unsuccessful applications and send replies at the end of the recruitment process, which is, in my opinion a warning sign that the recruitment agency could be blacklisted for not recruiting professional recruiters.

Research indicates that speed reading may affect the quality of their judgement.

On other occasions the recruiters may ask for questions, appointments, and, attending interviews. It is common for job recruiters to propose office hours which may be inconvenient for any person working office hours, and, this means that the user might wish to inform the recruiter automatically via email, or send him an SMS on his mobile phone to ensure that the recruiter reads the message.  

A script based reply which provides information about the user's availabilities might have been prepared in response to the automatic reply from the recruiter, and, similar templates might be thought of based on the reply.

This is because it is known that email boxes are crammed with emails and this creates a stigma for office workers including recruiters from reading certain emails, and, may have enabled rules within their email application to discard emails.  One has to appreciate the advanced functionality available even through using free web-based email such as Microsoft Hotmail, and, other email servers such as Microsoft Exchange or others.  

Please do not ignore my email because I mentioned the M-word, it is just an example.


What languages and technologies would you suggest using for coding the above scenario, if I had to code this from scratch?

Is software already available that I can just plug, play and configure to do the above?

---

### Post by stderr on 2012-07-04
I don't usually try to put people off bold ideas, but I strongly suggest you don't try this.

Starting from scratch, developing all the functionality you described, would probably take years, and still wouldn't be anything like you envisage. I somewhat doubt it would even become useful.*The reasons why are too numerous to mention (but to start you off - captchas, language interpretation, such a vast array of different target systems, the difficulty in replicating systems for testing, etc etc).

What is possible is little helpers to speed up parts of the manual process, such as limited form autocompletion, which already exists in many browsers (either natively or via plugins). Other things such as autoclicking and pasting macros are easy, but probably of limixed utility.

But, ask yourself this: with the volumes of applicants you describe, wouldn't one be much better off spending time targeting individual applications to each employer and role, rather than spamming everybody with generic applications which are much more likely to be rejected on first sight (and essentially get one blacklisted from that employer)?

All the best.

---

