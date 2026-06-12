---
title: "Access Permission"
date: 2009-08-31
forum: General Help
---

### Post by Rakesh.Parimkayala on 2009-08-31
Hi guyz, 
M just new to Ubuntu. Learned PHP and written some programmes in Windows environment. But I am facing trouble in executing the code in Linux environment. I located the root folder which we call the webserver(localhost) but could not paste the documents in that folder. some how used gksudo nautilus and pasted but when i type [http://localhost/UploadFIST/]("http://localhost/UploadFIST/%28all") (all the data is in uploadfist directory) showing an error messages 
**Forbidden**

 You don't have permission to access /UploadFIST/ on this server.


What should i do. Plz be in simple words, as I am the first time user in Linux. Much used to Windows environment and facing trouble working with linux..


Any help is much appreciated.
Thanks
Rakesh

---

### Post by SoftwareExplorer on 2009-08-31
You'll want to do this: ALT+F2, put ```
gksudo nautilus
```. Hit run. 
You will probably find your self in a folder called /root. Hit up until you are in the folder called '/', then go to 'var' and then 'www'. Select the files you want to allow access to and right click them. (This probably includes UploadFIST) Go to properties and then the permissions tab. Change the owner to 'www-data' and the group to 'www-data'.
Hope that helps. Go ahead and close all the windows we opened. Should work now.
If I doesn't, you may have to repeat this procedure, but go into UploadFIST and select all the files inside it instead.

---

### Post by SoftwareExplorer on 2009-08-31
By the way, welcome to Linux, Ubuntu, and the ubuntu forums.  :P

---

### Post by Rakesh.Parimkayala on 2009-08-31
[SIZE=4][COLOR=DarkOrange]Hi Thank you very much for your help and greetings. Nice welcome[/COLOR][/SIZE][COLOR=DarkOrange]..[/COLOR]

It worked if I change the permissions for each file instead of folder. But there are nearly 50-60 files. Its really gonna eat away all time time and really impossible..[SIZE=3]Any other approach you reckon??[/SIZE]

Also could you please suggest me any tutorials which will guide me through getting knowledge in LINUX. Coz every time I google up any installations on LINUX/UBUNTU they suggest some code like **[COLOR=Red]sudo get-apt xyz...something[/COLOR]**. Doesnt even know what the operation is and really gets annoyed by looking @ them and scares to leave this OS. 
I understood the term sudo/su but just want to know how many commands are there like these..How many can I remember? 

I found couple of video tutorials in Youtube describing the basic commands. but not in deep. Where can I obtain the information regarding this.

Please suggest me [SIZE=3][COLOR=Blue]
Which one among the GUI or teminal commands to start with???[/COLOR][/SIZE]

---

### Post by fluffman86 on 2009-08-31
When you are changing the permisions of a folder, you can change all the files in that folder at the same time by clicking the "apply permissions to enclosed files" button near the bottom of that window.

And don't worry about "learning" the command line like you would learn python or PHP.  Just do what you know how to do, look up what you don't know, pay attention to what you copy/paste in there, and eventually it will come to you just like learning your native language.  Babies don't sit through classes to learn how to talk, they just pick it up from the people around them.

Here's a few things just to start you off:
cd = take you to your home directory
cd Documents = take you to your Documents folder (assuming you're in your home folder already)
cd /etc = take you to /etc
cd ~/Music = take you to your music folder in your home folder.
cd .. = move up a directory
ls = list files and folders
ls -la = list ALL (including hidden) files and folders, with permissions
cp file1.txt ~/Documents/file2.txt = copy and paste and rename file1 from your current directory to file2 in your Documents folder
cp -r foldername ~/Documents = copies a folder and it's contents
mv = move a file or folder using the same syntax as above
rm = delete a file or folder as above

That should be it for now.  After that you can just learn as you go.

also: [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by SoftwareExplorer on 2009-08-31
Well, you could run 'sudo chown -R www-data:www-data /var/www'. I usually try to tell people how use the GUI first, but it's easier to do a batch of files in this case with the terminal.

---

### Post by Rakesh.Parimkayala on 2009-09-01
Thanks guyz..It worked if I change through terminal. But could not do it through GUI. I tried to change the permission of folder as in the screenshot. 
Any ways its working..Thank you guyz...

---

### Post by SoftwareExplorer on 2009-09-01
Your Welcome. :P 
Happy Ubuntu-ing!

---

