---
title: "How do I write a script to email people from a spreadsheet?"
date: 2009-10-17
forum: General Help
---

### Post by jon.reeve on 2009-10-17
I'm a university teacher, and I keep my grades in an OpenOffice spreadsheet file. What I want to do is, email each of my students (their email address are also in this spreadsheet) with their grades. Is there a way I can write a script to do that? I figure, this is Linux, right? There's got to be a way to do cool stuff like that with the command line.

---

### Post by StuartN on 2009-10-17
> **jon.reeve said:**
> Is there a way I can write a script to do that? I figure, this is Linux, right?

Yes. If you really want to write a script then install a command-line email client like Mutt. Configure it with your outgoing mailserver details.

Save your student file as a CSV (comma separated value) file and run a script to read each line, assign it to variables (one of which is the email address) and run mutt for each one:

```
while IFS=, read name email grade
do
  echo "Dear "$name"\n your grade is"$grade | mutt -s "Your grades" $email
done < "student_results.csv"
```

Explanation: While there is input, read a sequence of three values separated by the input separator "," from a file into name, email and grade. Call mutt with the subject "Your grades", echo a greeting with the student's $name and $grade into the body and send the message to $email.

Warning: I have not tried it. It relies on having exactly three tokens per line. Any error and the grade and student may misalign causing the details to be sent to the wrong addressee.

---

### Post by Johnny B on 2009-10-17
[SendEmail]("http://caspian.dotconf.net/menu/Software/SendEmail/") is an excelent command-line email script that could be used instead of mutt

---

