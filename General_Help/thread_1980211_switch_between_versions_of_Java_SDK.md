---
title: "switch between versions of Java SDK"
date: 2012-05-14
forum: General Help
---

### Post by dbclinton on 2012-05-14
I've got Java version 1.6.0 (IcedTea6) running on 10.04 but I need to use the SDK compiler from version 1.4.2. I downloaded and installed j2sdk 1.4.2 and used G Alternatives to switch Jar, JAVA and JAVAC to the 1.4.2. Nevertheless, even when I try JAVAC in the appropriate /bin folder, I still get the following error message:
> Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
I've even tried renaming
> /usr/lib/jvm  
just to get it "out of the way" - but nothing has helped. 
Any ideas?
David

---

### Post by QIII on 2012-05-14
Just as a developer, may I ask why you want to use a version of Java that is insecure and well beyond its end of life?

---

### Post by dbclinton on 2012-05-14
My son is actually taking a Java programing course and his teacher only accepts code that will compile on 1.4.2 - and you might be surprised at the annoying differences. :)

---

### Post by QIII on 2012-05-14
If I have a chance, I will try to get you an answer when I have a little time.

But from the standpoint of a developer, I would say your son's teacher is beyond foolish or is too lazy to update his syllabus.  Using JDK 7 U4 costs him nothing and places his students in a modern environment.

4 and 5 are dead and buried.  The funeral for 6 will be this fall. 

Your son is not well served learning to create a living creature from musty bones.

---

### Post by dbclinton on 2012-05-14
> If I have a chance, I will try to get you an answer when I have a little time.

Thanks. I really appreciate it!
> But from the standpoint of a developer, I would say your son's teacher is beyond foolish or is too lazy to update his syllabus. Using JDK 7 U4 costs him nothing and places his students in a modern environment.
I'm on your side.

---

### Post by QIII on 2012-05-14
I'm tutoring a C++ student tonight, but might be able to work this in.  Not difficult, but you know how it is...

BTW, is he using an IDE like Netbeans?

---

### Post by 1clue on 2012-05-14
I develop on the Java virtual machine for a living.

There are several problems with older JDKs which make that JVM beyond obsolete.  There are severe security vulnerabilities with it, and there are enough changes in 1.5 and up that learning things on 1.4 is essentially worthless.

There is no legitimate excuse for not upgrading.  Every developer environment which works with 1.4 is better with 1.6 or 1.7.  Best practices have changed to match the features of the JVM and the compiler.

I'm pretty sure I found a picture of your instructor:

---

### Post by QIII on 2012-05-14
Great picture.  A classic.  But in this case I think the instructor is past his shoulders.

Downright COUNTERproductive and a real disservice to his students.

---

### Post by dbclinton on 2012-05-14
> BTW, is he using an IDE like Netbeans?

No. He's working in Gedit (one of my favorite pieces of software).

---

### Post by dbclinton on 2012-05-14
> There is no legitimate excuse for not upgrading. Every developer environment which works with 1.4 is better with 1.6 or 1.7. Best practices have changed to match the features of the JVM and the compiler.
As a (non-tech) teacher I can sympathize with him. The curriculum would require extensive rewriting...and I'm not sure that he is even the one authorized to do it. This really isn't so bad: I was reading through the base curriculum document (from the Ministry of Education of Ontario) and it looks almost unchanged from when I took the course...in 1977!!! 
At least this teacher has updated from Fortran!

---

### Post by 1clue on 2012-05-14
> **dbclinton said:**
> As a (non-tech) teacher I can sympathize with him. The curriculum would require extensive rewriting...and I'm not sure that he is even the one authorized to do it. This really isn't so bad: I was reading through the base curriculum document (from the Ministry of Education of Ontario) and it looks almost unchanged from when I took the course...in 1977!!! 
At least this teacher has updated from Fortran!

I need to rage against the machine.

These students are paying good money to learn what they need to know to be productive software developers when they get out of college.  In most cases these people don't have extra money to spare, or worse yet they're using your money and my money in the form of grants and loans.

There is a lot of good material out there in the public domain for Java education and most of the hundreds of languages that run on that VM.  Grab some of that and apply your education to it, and you'll get a perfectly adequate college level curriculum.

@dbclinton,

I strongly urge your son to go get a current version of Eclipse or STS or NetBeans or whatever else you want to use, and the latest JVM, and do a little overtime to figure out the differences.

Or better yet, count on going to a seminar like No Fluff Just Stuff when he gets out.  It's going to be more expensive than the college course but it's definitely worth it.  You get 3 or 4 days of intensive brain dump from guys who either helped develop the software the class is about or is extremely good at teaching it.

[http://nofluffjuststuff.com/home/main](http://nofluffjuststuff.com/home/main)

If that's too rich for your blood, then try a cheaper one.  Or some online tutorials like I recommended above.

I have to seriously question the curriculum that can't see to update itself in a situation like you describe.  Even if it isn't in the teacher's hands, whoever is ultimately responsible is a paper pusher of the lowest caliber.

---

### Post by dbclinton on 2012-05-15
> I have to seriously question the curriculum that can't see to update itself in a situation like you describe. Even if it isn't in the teacher's hands, whoever is ultimately responsible is a paper pusher of the lowest caliber.

The truth is that, despite some structural problems, the course wasn't too bad at all. My son has a much better grasp of coding principles than when he started. 
It was, by the way, a high school course delivered on line (virtualhighschool.com).

---

### Post by 1clue on 2012-05-15
Maybe I'm showing my age and inflexibility.

In my mind, the larger the audience for a class, the more necessary that the curriculum be up to date.

There is of course a certain lag to be expected, but given the age of the 1.4.2 JVM that excuse holds no weight.  My company has upgraded all its Java software not once but twice since then, and is preparing to do so again for the 1.7 stuff.

---

