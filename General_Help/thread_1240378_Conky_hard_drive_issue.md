---
title: "Conky hard drive issue"
date: 2009-08-14
forum: General Help
---

### Post by Maintech on 2009-08-14
I am setting up conky for my desktop. I have everything configured except for the temperature of my 4th hard drive. I have tried everything to try and get it to work and so far I have been unable. I have attached a picture of my conky.

Here is my code:
${color white}Hard Drive Temperatures:
 ${color}hdd Vista $alignr /dev/sda ${color #FF6600}${execi 5 nc localhost 7634 | cut -c26-27 ;}C
 ${color}hdd Linux $alignr /dev/sdb ${color #FF6600}${execi 5 nc localhost 7634 | cut -c56-57 ;}C
 ${color}hdd Storage $alignr /dev/sdc ${color #FF6600}${execi 5 nc localhost 7634 | cut -c86-87 ;}C
 ${color}hdd Games $alignr /dev/sdd ${color #FF6600}${execi 5 nc localhost 7634 | cut -115-116 ;}C
 

Here is a copy of my nc command in a terminal:
|/dev/sg0|Maxtor 7V250F0|53|C||/dev/sg1|Maxtor 7V250F0|50|C||/dev/sg2|Maxtor 7V250F0|53|C||/dev/sg3|Maxtor 7V250F0|46|C||/dev/sda|Maxtor 7V250F0|53|C||/dev/sdb|Maxtor 7V250F0|50|C||/dev/sdc|Maxtor 7V250F0|53|C||/dev/sdd|Maxtor 7V250F0|46|C|

I have carefully counted and tried /dev/sg3 and /dev/sdd and neither will give a valid output to conky. As you can see the others work. Is there an issue with numbers above 99?

Any help would be greatly appreciated.



Found the issue. Changed /dev/sdd to /dev/sg3 and it worked.

---

