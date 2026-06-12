---
title: "Why no java6?"
date: 2010-05-03
forum: General Help
---

### Post by Zeemvel on 2010-05-03
Why don't any java6 jdk and jre packages work in Ubuntu 10.4?

Thanks.

---

### Post by inameiname on 2010-05-03
I installed Java6 this way:

sudo apt-get install sun-java6-fonts 
sudo apt-get install sun-java6-jre 
sudo apt-get install sun-java6-plugin 


...and it works just fine. Though, it seemed to have also installed OpenJDK, which is apparently the new Java program Ubuntu uses. They've given up on Sun I guess, though still have it in their repos. I'm not sure how old or new the repos version of Sun Java is though, but it works for me so I don't really care at this time. 

So I'm not sure why you are having trouble. How do you install them? Regardless, my guess is due to the new OpenJDK Java 6.

---

### Post by dragos2 on 2010-05-03
Sun JRE is the official one and that is the one all developers compile their code and test against. There are other runtimes for Java like OpenJDK supported by Sun as an open-source project, also some from IBM but the official one is Sun's JRE/SDK (now Oracle) which is used by 99% of Java programmers.

So please try to use the official jre/sdk especially if you are deploying enterprise java applications.

---

### Post by wojox on 2010-05-03
Here's what I use to install Sun Java [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by nanohead on 2010-05-03
I just don't know why this is such a colossal hassle each time there is a new Ubuntu release :confused:.   A total pain in the ****.

Its like brain surgery each time.   

My fave is that Synaptic has basically become such a garbage dump, that if you try and find something as fundamental as Sun Java in it, you get 9 million different things that are not relevant.

After many years of using Ubuntu pretty heavily, its getting more complicated and convoluted than our friends from redmond seem to make their software.....

---

### Post by Zeemvel on 2010-05-21
I thought Sun had open sourced everything from Java etc..., what reason is there for Ubuntu to do so difficult about Sun Java (And it is difficult for sure, it was hell to set it up, OpenJDK is not what we use here by the way).

---

### Post by CSInDevelopment on 2010-05-21
If you install the IDE netbeans it =appears to automatically install the sun jdk with it (pricks wont let me use netbeans with GCJ anymore)

Another interesting point:
Due to java bytecode not being as open source as we are lead to believe...any virus written in java will appear clean no matter how obvious, due to antivirus companies not having access to this, and as it runs on a virtual machine...I think this shows that if they dont let it open some time soon, it wont be used for security reasons

---

### Post by julio_cortez on 2010-05-21
> **inameiname said:**
> Though, it seemed to have also installed OpenJDK, which is apparently the new Java program Ubuntu uses.
Same here. I installed the kubuntu-restricted-extras assuming I would get Sun Java 6, but I got OpenJDK instead.

> **inameiname said:**
> sudo apt-get install sun-java6-fonts 
sudo apt-get install sun-java6-jre 
sudo apt-get install sun-java6-plugin
Thanks, I'll try those when I get home. I'm developing a small Java application and I'd like to be sure it can run with Java Sun (which is the one we're using here at work).

---

### Post by Irihapeti on 2010-05-21
You will need to have the "Partner" repository enabled to get Sun Java. It's in System -> Administration -> Software Sources -> Other software, or the equivalent for KDE.

---

