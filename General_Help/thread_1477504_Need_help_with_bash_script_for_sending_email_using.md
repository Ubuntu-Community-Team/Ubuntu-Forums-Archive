---
title: "Need help with bash script for sending email using mailx; I CAN do it in the terminal"
date: 2010-05-08
forum: General Help
---

### Post by Asfastasdark on 2010-05-08
Hi everyone,
I'm trying to send an email using mailx, in a bash script, but I can't get it to work. In the terminal I can, and this is how I do it:
```
$ mailx johndoe@gmail.com
Message
^D
```

Within seconds of doing this, I get sent an email. The problem is with the bash script I'm trying to make. Among other things, I tried this:
```
#!/bin/bash
mailx johndoe@gmail.com < "Message"
```

I honestly don't know what I'm supposed to do, and I've Googled a bunch of things too, and didn't have too much luck. Is there anyone who could help me out?

Edit: Figured it out. This is what I did, and it works for me:
```
#!/bin/bash
echo "Message" | mail -s "Subject" "johndoe@gmail.com"
```

---

### Post by lmarmisa on 2010-05-08
Mailx reads its input from the standard input stream stdin.

If you wish to send a mail that is prepared in a text file, then write your message with your preferred editor (vi, gedit, etc) and save it in a file (for example message.txt).

Type this command if you wish to send this message:

> 
mail [EMAIL="johndoe@gmail.com"]johndoe@gmail.com[/EMAIL] < message.txt
Other possibility is to use the redirection by means of a pipe. For example

> 
ls -l | mail [EMAIL="johndoe@gmail.com"]johndoe@gmail.com[/EMAIL]
In this case a message is sent with the output of the "**ls -l**" command.

Best regards,

Luis

---

### Post by Asfastasdark on 2010-05-08
Thank you Luis! But I just figured out a way that works for me as I only use this bash script for sending very short messages.

---

### Post by lmarmisa on 2010-05-08
You can use positional parameters in your script. 

For example, this could be the content of a script named mail_sort_message: 

> 
#!/bin/bash
echo $1 | mail -s "Subject" "johndoe@gmail.com"
and this is an example of use:

> 
./mail_sort_message "Hello, world!"


---

### Post by Asfastasdark on 2010-05-08
Cool. I'm relatively new to bash, as you can probably tell, but I have programmed in a few other languages. Can all scripts use paramaters like $1, $2, $3, etc.? And if so, what is the highest it goes up to? $9?

And I know this is a bit off-topic... but if I wanted to send a message that said, say, "Today is [date]!", could I somehow do:
```
#!/bin/bash
echo "Today is " + date + "!" | mail johndoe@gmail.com
```
?

---

### Post by mrowth on 2010-05-08
> **Asfastasdark said:**
> Cool. I'm relatively new to bash, as you can probably tell, but I have programmed in a few other languages. Can all scripts use paramaters like $1, $2, $3, etc.? And if so, what is the highest it goes up to? $9?

And I know this is a bit off-topic... but if I wanted to send a message that said, say, "Today is [date]!", could I somehow do:
```
#!/bin/bash
echo "Today is " + date + "!" | mail johndoe@gmail.com
```
?

You can use "backticks" (``) to run a command and insert its output:

$ echo "Today is `date`!"
Today is Sun May  9 03:58:00 CEST 2010!

---

### Post by lmarmisa on 2010-05-08
Bash is the heir of the old Bourne shell of Unix. It's a very powerful script language.

A few references:

[http://tldp.org/LDP/Bash-Beginners-Guide/Bash-Beginners-Guide.pdf](http://tldp.org/LDP/Bash-Beginners-Guide/Bash-Beginners-Guide.pdf)

[http://tldp.org/LDP/abs/abs-guide.pdf](http://tldp.org/LDP/abs/abs-guide.pdf)

[http://www.gnu.org/software/bash/manual/bashref.pdf](http://www.gnu.org/software/bash/manual/bashref.pdf)

---

### Post by Asfastasdark on 2010-05-08
Thanks guys, just from what I've seen so far, Bash is awesome. I just did this:
```
#!/bin/bash
echo "[`date '+%F %T'`] date and mailx test." | mail "johndoe@gmail.com"
```

I also figured out that Bash can display the time up to a billionth of a second (and it wouldn't surprise me if it could go even further).

And Luis, thanks for those guides, I'll definitely be reading them.

---

### Post by lmarmisa on 2010-05-08
I have more information about bash (but I am not really an expert ;)). Do not hesitate to send me a private message if you need this information.

Best regards,

Luis

---

