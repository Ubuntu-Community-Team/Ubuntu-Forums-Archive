---
title: "Medical Software?????"
date: 2009-07-10
forum: General Help
---

### Post by shuukazedojo on 2009-07-10
Hello. I'm looking for some software to help in the operation of my medical practice. We really only need some basic functionality: financial accounting, insurance printing and management; and patient records. Is there anything like this out there???

We were using a very expensive M$ based program, but we'd love to go full Ubuntu in the new office. 

Thanks for the info!

---

### Post by jiraaya on 2009-07-10
What are the exact software that you are using? if you need just the basic functionality, why don't you try open-office?

---

### Post by nice_like_rice on 2009-07-10
If it's something microsoft money, kmymoney and gnucash are good alternatives.

Which ms program are you using?

---

### Post by csabo2 on 2009-07-10
i would say use an open source CMS like SugarCRM..ect  that would cover you.

---

### Post by shuukazedojo on 2009-07-25
Right now we use a program called Chirosoft. It provides the functionality of patient management, insurance form printing and management, as well as patient notes (although this function is unnecessary). 

SugarCRM looks closer to what we need than a bunch of Open Office stuff, but it still lacks the insurance form printing. I imagine it would manage the patient files, but the two functions really need to be integrated for efficient functionality. Any more ideas?

Thank you so much for your responses!!!

---

### Post by slacker1965 on 2009-09-27
Nothing?  Nothing specifically for physicians?  Bump!  I am curious about this, too.  Is this something else that Microsoft is going to get an anchor in without anything from the Ubuntu community, or the larger Linux community?  Please say it ain't so...

---

### Post by shuukazedojo on 2009-09-27
I'm with you slacker! I do everything I can to stay away from winbloze and anything proprietary. This piece of software is a huge part of our office flow and right now it seems like it is M$ dominated. We are supposed to be receiving some demos of various software soon. I will try to run them through WINE or a virtual box if they aren't Linux native. 

We would love to hear from the physician/therapist community!!! There has to be something out there! Whatever happened to the distro built specifically for physicians? What ever happened to the software that came with it?

---

### Post by perspectoff on 2009-11-07
Ubuntu Doctor's Guild -- [http://www.ubuntudoctorsguild.org](http://www.ubuntudoctorsguild.org)

---

### Post by mo.reina on 2009-11-07
i would check out [http://www.islandcoders.com]("http://www.islandcoders.com")

they already have some pre-existing software that would need minimal adjustments, if any, for your needs.  they've done a lot of work with farms, vet clinics, and released a small app on the palm platform for doctors.

---

### Post by shuukazedojo on 2009-11-07
Thanks for the info!!!

---

### Post by gouravshah on 2009-12-14
check out [http://www.clear-health.com](http://www.clear-health.com)

---

### Post by FinalCoyote on 2009-12-29
Funnily [http://www.ubuntudoctorsguild.org](http://www.ubuntudoctorsguild.org) only has windows EHRs, or linux-server, windows-client ones...
Hmm, this is an interesting problem...

---

### Post by pbrane on 2009-12-29
Have you looked at [OpenEMR]("http://www.oemr.org/") ?

---

### Post by kilee on 2009-12-30
[http://wiki.gnumed.de/bin/view/Gnumed](http://wiki.gnumed.de/bin/view/Gnumed)

---

### Post by nechus on 2009-12-30
Have a look at [www.google.com/health](www.google.com/health)

---

### Post by bertmanphx on 2010-01-01
Have you looked at OpenEMR?

bertmanphx

---

### Post by shuukazedojo on 2010-01-20
OpenEMR doesn't really fit our needs very well. It's a little too involved and specific. Our office is more therapist oriented than doctor. 

Just downloaded Gnumed. It may have potential since it's at least an active project, but it looks like the billing function is not yet functional.

Thank you everyone for the replies!!! Please, keep them coming!

---

### Post by supershin on 2010-01-20
^ I second that motion. Very interesting stuff here.

---

### Post by supershin on 2010-01-28
> **shuukazedojo said:**
> OpenEMR doesn't really fit our needs very well. It's a little too involved and specific. Our office is more therapist oriented than doctor. 

Just downloaded Gnumed. It may have potential since it's at least an active project, but it looks like the billing function is not yet functional.

Thank you everyone for the replies!!! **Please, keep them coming!**  

....

---

### Post by Leppie on 2010-01-28
you may find some interesting stuff here: [http://www.goomedic.com/linuxforclinics-medical-ubuntu-project.html](http://www.goomedic.com/linuxforclinics-medical-ubuntu-project.html)

---

### Post by fishydoc on 2010-01-30
Look also at OpenMRS, and GNU cash. Check the Riegenstrieff Institiute of health informatics. they are very helpful.

---

### Post by fishydoc on 2010-01-31
Gnumed was not ready for billing , had plenty inconsistencies and not very user friendly and for follow up it was very annoying to have all the symptoms over time on one page, one page with observations over time, actions similar and plans. To many clicks to get what I wanted and annoying typeset The SOAP concept can be better used. This was very annoying unless they have imporved over the last 8/12. another problem was some of the conceptdictionary items.

Now very happy with setting up openMRS, you can make it as specific as you like.
You can make  and adjust your own concept dictionary to allow for billing or health and safety purposes and any type of practice.

---

### Post by fisheater on 2010-01-31
Here is a beauty from Canada:

[http://www.oscarcanada.org/](http://www.oscarcanada.org/)

These are showing great promise, I hope they continue to grow. The current propitiatory EMRs are generally very average with little customization to make them close to useful. We can put a man on the moon, bake bread on our countertops but still languish with cumbersome EMRs. 

The other frustrating aspect of those closed systems is that the database they employ to store data is closed, non-portable, and not easily moved into another EMR.

Thanks for some of these links, I had not seem them previously.


FE

---

### Post by samMD on 2011-05-19
So I tried Installing openemr and then left my computer I set it to sleep after 2 hours and it did not knowing if openemr is installed or not. 

but the problem is I went to go install GNUmed and the install button is greyed out b/c of an error with openemr:

E:I wasn't able to locate file for the openemr package. This might mean you need to manually fix this package.: 

anyone know how I can fix this package?

---

### Post by Maheriano on 2011-05-19
I own a company which makes high end software solutions for businesses, we could make you something like this if you're interested. And we can write it in either operating system you choose.

---

### Post by bertmanphx on 2011-05-20
SamMD,
If you plan on using OpenEMR, I would install it within a LTS release like Ubuntu 10.04, not 11.04.  Did you try running it from the command line?  If so,  it may give an error that can track down the problem.  I've installed it here for testing purposes with no problems.

bertmanphx

---

