---
title: "pbnj 2.0 Error in option spec"
date: 2010-07-28
forum: General Help
---

### Post by ertrifo on 2010-07-28
Noob question!

I've installed pbnj 2.0 with the command "sudo apt-get install pbnj" on ubuntu 10.04
I can successfully scan hosts with the command scanpbnj

Eg. 
>scanpbnj 192.168.0.11
--------------------------------------
Starting Scan of 192.168.0.11
Inserting Machine
Inserting Service on 135:tcp msrpc
Inserting Service on 139:tcp netbios-ssn
Inserting Service on 445:tcp microsoft-ds
Scan Complete for 192.168.0.11
--------------------------------------

The scan results are being saved in ~/pbnj-2.0/data.dbl

Could please someone tell me how to query the database (data.dbl) because I'm getting errors every time I run a query included in the ~/pbnj-2.0/query.yaml file

example query: 
>outputpbnj -q sdump
Error in option spec: "test|=s"
Error in option spec: "debug|=s"

I must be doing something wrong because this is happening for every query

Thanks in advance :)

---

### Post by Fonze on 2010-08-11
You will need to edit the outputpbnj file located in the /usr/sbin/ directory. You can search for the following text within the file.

[LIST]
[*]test|=s
[*]debug|=s
[/LIST]
This can be done by typing:** /test|=s** or [B]/debug|=s.
[/B]
A quick observation of the format of the options will lead you to removing the "|" symbol from test|=s and debug|=s. Once this is done these options should look like this **'test=s' **and **'debug=s'**. 

Save the changes and run the query. As always be sure to make a copy of the file before editing the original.

---

