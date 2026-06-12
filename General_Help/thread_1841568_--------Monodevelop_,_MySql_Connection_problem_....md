---
title: "--------Monodevelop , MySql Connection problem ...Pls Help--------"
date: 2011-09-09
forum: General Help
---

### Post by SatishSql on 2011-09-09
Hello, 
I am quite new to Mono and MySql , pls ignore if I sounds something silly. 

I am trying to connect to MySql , just following this thread  [http://www.mono-project.com/MySQL](http://www.mono-project.com/MySQL)  
and had following problems 

>>> While installing Installing MySql.Data.dll in the GAC by executing   

gacutil -i MySql.Data.dll , 

i got the message 

"Failure adding assembly MySql.Data.dll to the cache: gac directories could not be created, possibly permission issues." 

Then i tried :     

sudo gacutil -i MySql.Data.dll   

and got the message   

"Installed MySql.Data.dll into the gac (/usr/lib/mono/gac)" , 

It was looking fine  , so I continued  and.. 



>>> tried to execute the program as mentioned in the thread, 

mcs TestExample.cs -r:System.Data.dll -r:/path/to/MySql.Data.dll 

but I got the  "error CS0006: cannot find metadata file `/path/to/MySql.Data.dll' " 


Please help. 

Thanks, 
Sat.

---

### Post by directhex on 2011-09-10
You're substituting "/path/to/" with the actual path... right?

---

