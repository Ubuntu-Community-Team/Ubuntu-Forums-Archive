---
title: "email (msmtp) not working"
date: 2012-01-02
forum: General Help
---

### Post by anon0 on 2012-01-02
Problem: I'm not receiving the emails that were sent using msmtp.

Details: msmtp seems to be an easy way to have the server send emails out. I followed the following tutorial:
[http://ubuntuforums.org/showthread.php?t=1185134](http://ubuntuforums.org/showthread.php?t=1185134)

And got up to:
echo "This is a test e-mail from my server using msmtp!" | msmtp -d [email]youremail@domain.com[/email]

It executed without apparent errors, returning "mail accepted for delivery" and "bizsmtp closing connection". But I'm not getting the emails. 

I did have to change the setting to "auth off" because otherwise I get "the server does not support authentication" and "could not send email".

Ideas?

---

### Post by anon0 on 2012-01-02
Anyone understands how the bottom line works? That gpg thing looks like it might be a solution.

[http://msmtp.sourceforge.net/doc/msmtprc.txt](http://msmtp.sourceforge.net/doc/msmtprc.txt)

# The SMTP server of the provider.
account provider
host mail.provider.example
from [email]smithjoe@provider.exampl[/email]e
auth on
user 123456789
passwordeval gpg -d ~/.msmtp.password.gpg

---

