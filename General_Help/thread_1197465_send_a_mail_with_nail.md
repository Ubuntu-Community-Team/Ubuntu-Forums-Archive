---
title: "send a mail with nail"
date: 2009-06-26
forum: General Help
---

### Post by b-boy on 2009-06-26
Hi guys I want to send a mail with nail which I can do with the following command ```
mail -s 'test' myself@gmail.com < **etc_hosts.txt**
```

but I dont want to have a file that needs to sent as the message I just want to type a message with out piping a file 

how can i do this?

---

### Post by t0p on 2009-06-26
Are you talking about the command-line program called **mail**?  If so, what you want to do is simple to achieve.  Open a terminal and type in

```
mail myself@gmail.com
```

You will be prompted for the email's subject-line.  Type in whatever you want and press Enter.

You are now confronted with a flashing cursor.  Type in the body of your email.  You can use the Enter button when you want to start a new line/paragraph.

When you've finished, start a new line (by pressing Enter).  Then type a '.' (full stop/period/whatever you call the damn thing) by itself.  Press Enter again.

Now you're prompted for a carbon-copy ('Cc:') address.  Type in the appropriate address or, if you don't want to send a carbon-copy, just press Enter.

Now, press Enter again.  The mail program exits and you are returned to the usual bash prompt.  Your mail is sent! (Assuming, of course, that your machine is configured to work as a mail server.)

Mail has more options than what I've outlined.  Typing into the terminal the command

```
mail --help
```

will give you a brief outline of the available options.  The program's manpage will spell it all out in more detail.

---

