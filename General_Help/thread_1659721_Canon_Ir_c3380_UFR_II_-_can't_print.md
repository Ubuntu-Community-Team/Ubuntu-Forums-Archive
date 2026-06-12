---
title: "Canon Ir c3380 UFR II - can't print"
date: 2011-01-04
forum: General Help
---

### Post by potetox on 2011-01-04
Hi everyone,

I've been trying to print with a Canon Ir c3380 UFR II printer without any success. I'm running Ubuntu 10.04.

So far here's what I've tried :
- get drivers from [http://fr.software.canon-europe.com/products/0010370.asp](http://fr.software.canon-europe.com/products/0010370.asp) (which is a newer version than the one indicated here : [https://wiki.ubuntu.com/HardwareSupportComponentsPrintersCanon](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersCanon))
- install printer
- enable job accounting since we use it at my workplace
- set ID for job accounting (we don't use a password)

I don't get any error messages, everything looks ok except that my documents don't get printed.

Any help would be greatly appreciated! I'm the first one to switch to linux at my workplace, I hope not to be the last one but it won't do if printing is not possible...

Thanks!

Julie.

---

### Post by potetox on 2011-01-05
Well, things are getting better but I'm not quite there yet.

I tried using CUPS : I uninstalled my printer and installed it again with CUPS. I did the thing to get job accounting enabled and I set my ID.

I can now print using "sudo lp ...". Better than nothing I guess. Still not a good way to convince other people to switch to linux. If I try not in sudo mode, I get a lot of black pages... 

Any ideas? Am I forgetting something?

I'll be grateful for any help!

---

### Post by potetox on 2011-01-05
Right, I'm doing the questions and answers...

It seems to work now. I didn't change anything though.

Could a reboot have done the trick? Or is it that some formats print ok while others don't?

So many mysteries!!

---

### Post by pirulo on 2011-03-16
After installation, you have to enable job accounting as root:

```
cnjatool -e [Printer Name]
```

Then in the user account, you have to set ID and password:

```
cnjatool -p [Printer Name]
```

Leave password blank if no password.

---

### Post by forevertheuni on 2012-09-12
Hi. I installed the new Canon Drivers(the ones available in Canon Site).
It is CQue 2.0.3 Linux Driver DEB 64-bit (v2.0.3)  
So I installed the printing by the system-config-printer ( I don't have cnjatool) The printer is well installed It's an IR C3380i. I can see the toner levels. I have 3 fields User ID User Password and Auth password...I don't know which ones to use(but tried everything already). 

I don't know where to enable Job Accounting.

I Print. It goes to the printer (I can see it in the log) but something is wrong. The status is "NG".

Once I could see that my USerID went OK in one of the printings(I saw it in the printer job details). 
But nothing comes out. Plz help.

I somewhat found a "Disable Job accouting for B&W" that actually is the policy of the place I work.

---

