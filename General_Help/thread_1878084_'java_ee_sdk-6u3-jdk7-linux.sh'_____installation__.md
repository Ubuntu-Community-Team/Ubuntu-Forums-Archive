---
title: "'java_ee_sdk-6u3-jdk7-linux.sh'     installation    help"
date: 2011-11-09
forum: General Help
---

### Post by weasels on 2011-11-09
Hi,
i have installed jre 6 u26 on my system and run the test java program in my browser and it runs fine.
Now i want to install the jee-jdk '.sh' file using "./java_ee_sdk-6u3-jdk7-linux.sh" but is asking to set up java environment variable.
Kindly help me how to set it 
~~~~~~~ without the earlier version setup details already available. i.e.
 """ $ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk """ 
since jee-jdk7 is a .sh file - manual installation binary.
thx

---

### Post by ~!geek!~ on 2011-11-09
> **weasels said:**
> Hi,
i have installed jre 6 u26 on my system and run the test java program in my browser and it runs fine.
Now i want to install the jee-jdk '.sh' file using &quot;./java_ee_sdk-6u3-jdk7-linux.sh&quot; but is asking to set up java environment variable.
Kindly help me how to set it 
~~~~~~~ without the earlier version setup details already available. i.e.
 &quot;&quot;&quot; $ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk &quot;&quot;&quot; 
since jee-jdk7 is a .sh file - manual installation binary.
thx

 Have you added the JAVA_HOME variable in your ~/.bashrc file if not you can try adding following in it..
export JAVA_HOME="completeaddress of jre/bin/java" 
Also in the line saying  
export PATH="/usr/local/bin............"  you may append  
addressofjredirctory/bin to it by starting it with a colon ( : )  
Now run the command "source ~/.bashrc" 
Try again running the sh file again and it should work.. If it does not check if permission for executing it is set.. 
To confirm just run the command: chmod +x ./jeefilename.sh and try again.. 
See if it helps!!

---

