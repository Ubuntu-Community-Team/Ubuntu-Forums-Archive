---
title: "permission problem: Cant copy file"
date: 2011-10-06
forum: General Help
---

### Post by HLS69 on 2011-10-06
Hello everyone,

I ve a file called client_key.pem and the file is located in \

Now I want to copy the file to my userspace (non root) desktop.
To clarify: my username is HLS69 and I want to copy the file to HLS69s desktop.

When I am in nautilus and want to drag and drop the file onto the desktop I get an error message:

Error opening file: Permission denied


Can anyone give me a brief introduction on how to copy the named file please?

---

### Post by dethorpe on 2011-10-06
I suspect that as the file is in root, its been copied there by root and your user dosn't have permissions to read it.
 
Go to the terminal and do this:
 
```
 
sudo cp /client_key.pem /home/HLS69
sudo chown HLS69 /home/HLS69/client_key.pem
chmod 664 /home/HLS69/client_key.pem
 

```
 
This will put a copy of the file owned by you in your home directory with read/write access, you can then move it from there to wherever you want it

---

### Post by coldraven on 2011-10-06
I think that this should work.
Open a terminal, Ctrl+Alt+T does it for me.
Type ```
gksu nautilus
```
Type in your password
You are now in root mode Nautilus and can drag drop, be careful what you do.
You might want to press F3 to get two panes, I find this to be easier.

---

### Post by HLS69 on 2011-10-07
> **dethorpe said:**
> I suspect that as the file is in root, its been copied there by root and your user dosn't have permissions to read it.
 
Go to the terminal and do this:
 
```
 
sudo cp /client_key.pem /home/HLS69
sudo chown HLS69 /home/HLS69/client_key.pem
chmod 664 /home/HLS69/client_key.pem
 

```
 
This will put a copy of the file owned by you in your home directory with read/write access, you can then move it from there to wherever you want it

thanks for your help, worked like a charm :)
I think if got to do a readup on how the commands you posted actually work.

@coldraven gksu with nautilus gave me the same error message I already experienced before but thanks for the F3 trick - didnt know that :)

---

