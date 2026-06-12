---
title: "bash coding help"
date: 2011-04-02
forum: General Help
---

### Post by kuraudo88 on 2011-04-02
I'm supposed to write a Bash program that
downloads WordPress, uncompresses the
files, moves them to a web-accessible
directory (diff. directory)

i'm new to Bash and I know I start writing the code with #!bin/bash 
what are the rest of the codes?
in terms of wordpress, i downloaded the zip file from the website and put in the server (linux ubuntu) using WinSCP
and i have created a file that ends with .sh in the same directory

could you help me out please?

thanks

---

### Post by cfbmoo1 on 2011-04-02
If you are using WinSCP.. sounds like you can just use the scp command and grab the file. As for unzipping it it's just a matter of using unzip.

So at the basic level...

#!bin/bash
scp <remote file> <local destination>
unzip <file>
mv <files> <destination>

Man pages should give you the details. You could also use CP to copy the files towards the end. It's up to you what you want to do in moving or copying.

---

### Post by Elfy on 2011-04-02
Sounds just like a homework thread. Please read the CoC 

> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.

Closed

---

