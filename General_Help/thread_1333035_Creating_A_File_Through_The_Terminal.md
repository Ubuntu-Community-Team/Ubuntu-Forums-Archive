---
title: "Creating A File Through The Terminal"
date: 2009-11-21
forum: General Help
---

### Post by Jforsyth on 2009-11-21
Hello,

I am new to Ubuntu/Linux and am trying to install torrentflux on my computer. The setup process requires that I create a text file in a certain directory within the /var/www folder.

I cannot create the file using the GUI or the save command in gedit because I apparently lack the permissions to do so. It seems like I have to use the terminal with the sudo command.

How would I go about creating a new file and saving it through the terminal? Is there any way that I can allow myself to create/edit files through the GUI?

---

### Post by CaKiwi on 2009-11-21
try 

sudo gedit /var/www/filename

---

### Post by sahabcse on 2009-11-21
Try the below also

#sudo touch filename
#sudo vim filename

---

### Post by Jforsyth on 2009-11-21
Thanks for the help, guys. That appeared to work.

However, I seem to have dug myself into a bigger hole now.

I tried to change the permissions of the /usr folder to 777 and inadvertently lost myself the ability to use sudo.

The message &#8220;sudo: must be setuid root" appears whenever I try to use it. A preliminary search of these forums and Google yields several ways to try and fix it, but none of them have worked.

I can't use sudo to chmod the correct file back, nor can I become the root to so it using "su". Not really sure what to do.

This is embarrassing.

---

### Post by sahabcse on 2009-11-21
login to the recovery mode and type the below command


#chmod 755 /usr

---

