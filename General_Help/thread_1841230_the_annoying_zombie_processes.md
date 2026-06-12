---
title: "the annoying zombie processes"
date: 2011-09-09
forum: General Help
---

### Post by bluesatbridge on 2011-09-09
Hi sir/madam  
i am a new ubuntu user switching 
i am using ubuntu 10.04 and recently i am starting to have problems of 2 zombie process
i was using firefox  5 and i was getting this message of update firefox but then it wont connect to the update so i downloaded the tar file and update it in the /opt directory
but since then i am having 2 zombie process 
out put of "top" command
top - 11:18:22 up 8 min,  3 users,  load average: 0.22, 0.29, 0.22
Tasks: 169 total,   3 running, 164 sleeping,   0 stopped,   2 zombie
Cpu(s): 25.0%us, 50.0%sy,  0.0%ni, 25.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2444148k total,   936496k used,  1507652k free,    48296k buffers
Swap:  5000188k total,        0k used,  5000188k free,   411092k cached
one is 
dhclient <defunct>
firefox-bin  <defunct>
now i understand zombie process are harmless and i can kill them with the kill -9 ppid but is there a possible way to get rid of them i mean get to the root cause and remove them because they come up every time i restart my laptop

Any help will be appreciated

cheers
shantanu

---

