---
title: "Problem using php mail call in 10.10"
date: 2010-11-18
forum: General Help
---

### Post by cearlp on 2010-11-18
The scenario is this:
An html form is displayed having several input fields and when the submit button is selected the form action is a PHP file.The PHP file gets the input fields and builds an email message and calls the PHP mail function.
It worked on 8.04 but doesn't work on 10.10.
No error is displayed but the email message that the script generates is never sent.
The statement is:  
     mail($to, $subject, $message, $headers);
with the variables having been set from the input fields.

Could there be certain PHP/mail software modules that I need to install?

---

