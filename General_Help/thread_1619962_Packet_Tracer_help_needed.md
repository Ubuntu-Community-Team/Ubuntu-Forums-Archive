---
title: "Packet Tracer help needed"
date: 2010-11-12
forum: General Help
---

### Post by tillerdemon on 2010-11-12
I have searched for the correct way to install Packet Tracer in Ubuntu 10.04, however I am having some difficulties doing it... I have downloaded "PacketTracer531_Ubuntu.tar.gz" it's sitting in my download file now, I am not sure if I am supposed to extract it now? If someone can please post the correct terminal commands to install this it would be greatly appreciated. I had previously downloaded it, then extracted it, opened the file and placed the Install.sh file in the terminal and ran it, it install fine but won't allow me to save files without crashing. I am sure it has to with me not installing it at root level? Thank You

I have tried: cd/home/mac/Downloads/PacketTracer531_Ubuntu.tar.gz and got this:
bash: cd/home/mac/Downloads/PacketTracer531_Ubuntu.tar.gz: No such file or directory

---

### Post by jonny-walker on 2010-11-15
From your question, you seem new to linux, what you typed was wrong, there is no such syntax as 'cd/home/mac/Downloads/PacketTracer531_Ubuntu.tar.gz' 

Note that 'cd' is a command, '/home/mac/Downloads/' is a path and 'PacketTracer531_Ubuntu.tar.gz' is a file. Your typing was wrong and this is why you got an error. Here is the way forward:
 

1. You need to extract PacketTracer531_Ubuntu.tar.gz
2. You need to make the file executable if it is not
3. You need to install the package as root

             Example
1. This command will change you current working directory to Downloads (don't include the quotes)
     'cd   /home/mac/Downloads/'   
2. This command will extract the archive  (PacketTracer531_Ubuntu.tar.gz)
    'tar -xzvf  PacketTracer531_Ubuntu.tar.gz'
3. After completing step 1 and 2 above , double click on the file '_install_' and click '_Run on terminal_' and installation will immediately start

---

