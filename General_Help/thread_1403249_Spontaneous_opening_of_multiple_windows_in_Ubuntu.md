---
title: "Spontaneous opening of multiple windows in Ubuntu"
date: 2010-02-10
forum: General Help
---

### Post by Hayksk on 2010-02-10
Hello.
I'm using Ubuntu 9.10. The problem is that very often, when I move the mouse without clicking any button, a lot of multiple windows (trash, add to panel, or other applications) are suddenly opened. This problem occurs very often and become very annoying. 
Can anybody help me solve this problem.

---

### Post by Satoru-san on 2010-02-10
Did you download any programs that were not in the repository? Did you download a script that someone told you to run?

It sounds like you have one of those malicious codes going on.

---

### Post by AlexDudko on 2010-02-10
It can also be a mouse problem. Can you try another one?

---

### Post by Hayksk on 2010-02-10
to [Satoru-san]("http://ubuntuforums.org/member.php?u=1015330")

I don't remember exactly, but perhaps yes.
It seems to me that my g++ compiler also doesn't work properly.
What can I do. Will any antivirus (Avast, foe example ) eliminate the problem?

---

### Post by Hayksk on 2010-02-10
> **AlexDudko said:**
> It can also be a mouse problem. Can you try another one?

On the same computer, when in Windows OS, no such problem occurs.

---

### Post by Satoru-san on 2010-02-10
> **Satoru-san said:**
> Did you download any programs that were not in the repository? Did you download a script that someone told you to run?
> **Hayksk said:**
> I don't remember exactly, but perhaps yes.

I need to know exactly, if you dont tell me then there is no way to know what is wrong.

> **Hayksk said:**
> It seems to me that my g++ compiler also doesn't work properly.

any details? error messages? what happens that makes you believe this to be so?

---

### Post by Hayksk on 2010-02-10
> **Satoru-san said:**
> I need to know exactly, if you dont tell me then there is no way to know what is wrong.



any details? error messages? what happens that makes you believe this to be so?

For example, when compiling the following c++ program and then running it, after entering 'x' - results in infinite loop:


#include <iostream>
using namespace std;

int main()
{
        int a;
        int b;
        cout << "Enter two integers for a and b: ";
        cin >> a >> b;

        while(  (a != 'x') && (b != 'x') )
        {
                cout << "a = " << a << ", b = " << b << endl;
                cin >> a >> b;
        }

        return 0;
}



After the following input in the command line:  8 x
Output is infinit loop:

a = 8, b = 134514912
a = 8, b = 134514912
a = 8, b = 134514912
a = 8, b = 134514912
a = 8, b = 134514912
a = 8, b = 134514912
a = 8, b = 134514912
a = 8, b = 134514912
a = 8, b = 134514912
a = 8, b = 134514912
a = 8, b = 134514912
a = 8, b = 134514912
a = 8, b = 134514912
a = 8, b = 134514912
a = 8, b = 134514912
a = 8, b = 134514912
a = 8, b = 134514912
a = 8, b = 134514912
------------------------------
continues infinitely

[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

---

### Post by Satoru-san on 2010-02-10
> **Hayksk said:**
> For example, when compiling the following c++ program and then running it, after entering 'x' - results in infinite loop:

        while(  (a != 'x') && (b != 'x') )
        
you do realize that a and b will never equal x
a and b are int
there is nothing wrong with your compiler.

Learn2code

So tell me what software did you recently install that was not in the repository?

---

### Post by Hayksk on 2010-02-10
> **Satoru-san said:**
> you do realize that a and b will never equal x
a and b are int
there is nothing wrong with your compiler.

Learn2code

So tell me what software did you recently install that was not in the repository?


testdisk-6.11.3.linux26

several firefox add-ons:

---

### Post by Satoru-san on 2010-02-10
firefox addons wouldnt do that and that program is legitimate. 

I cant help anymore without more details. Sorry. Good luck.

---

### Post by Hayksk on 2010-02-10
Thank you, Satoru-san.
Although the original problem not solved, I corrected my C++ code and now it does work correctly.

#include <iostream>
using namespace std;

int main()
{
        int a;
        int b;
        cout << "Enter two integers for a and b: ";

        while( cin >> a >> b  )
        {
                cout << "a = " << a << ", b = " << b << endl;
        }

        return 0;
}

---

### Post by rnerwein on 2010-02-10
> **Satoru-san said:**
> you do realize that a and b will never equal x
a and b are int
there is nothing wrong with your compiler.

Learn2code

So tell me what software did you recently install that was not in the repository?
hi 
that's not the problem about int and char. thats the way the function will handle the input. i preferr C and i think C++ is based on C. i think - cin >> a >> b; expect int as input, but what happens if it's not a int ? the other way is if you define a and b as a "char" --> same problem with the input. --> here is what work. even the input longer or
int or char or string.

#include <stdio.h>
#include <stdlib.h>
#define F_form "%s %s"
int main(int ac, char **av)
{
int i_a;
int i_b;
int i_i;
char ac_dummy[4096];
char ac_c[4096];
char ac_d[4096];

    while(( ac_c[0] != 'x') && ( ac_d[0] != 'x'))
    {
        fprintf(stderr," ====> input 2 interger or 'x' to end <=====\n");
        read(0,ac_dummy,sizeof(ac_dummy));
        i_i = sscanf(ac_dummy,F_form,ac_c,ac_d);
        i_a = atoi(ac_c);
        i_b = atoi(ac_d);
        fprintf(stderr,"a: %d  b: %d (len:%d)\n",i_a,i_b,i_i);
    }
exit(0);
}

===> C is like a razor blade but without a grip <====        ;)
ciao

---

### Post by Nunu on 2010-02-10
Will you or have you be / been able to test a different mouse on the system?

---

### Post by Pritamsng on 2010-02-10
problem is in hardware, O.S or driver. if you are using usb mouse the connect ps/2 mouse and check or vice-versa. Then you can know that problem is in hardware or in other. according to that you can try to solve your issue.

---

### Post by warfacegod on 2010-02-10
It possible that Dwell clicking is enabled in System> Prefs.> Mouse> Accessibility tab.

You may also want to look in and disable Assistive Technologies.

---

### Post by Hayksk on 2010-02-10
> **warfacegod said:**
> It possible that Dwell clicking is enabled in System> Prefs.> Mouse> Accessibility tab.

You may also want to look in and disable Assistive Technologies.

Dwell clicking is not enabled.
But how to disable Assistive Technologies?

---

### Post by warfacegod on 2010-02-10
> **Hayksk said:**
> Dwell clicking is not enabled.
But how to disable Assistive Technologies?

Go to: System> Prefs.> Assistive Technologies

Notice where my mouse is, if there is no check there, then it is already disabled. Check it then uncheck it to make sure.

---

### Post by Hayksk on 2010-02-10
Thank you, [rnerwein]("http://ubuntuforums.org/member.php?u=972890"), for your code...

---

### Post by warfacegod on 2010-02-10
Are you using a Touchpad or an actual mouse? If it's a mouse is it optical (laser)?

---

### Post by Hayksk on 2010-02-10
> **warfacegod said:**
> Go to: System> Prefs.> Assistive Technologies

Notice where my mouse is, if there is no check there, then it is already disabled. Check it then uncheck it to make sure.

I did exactly as you have shown, though assistive technologies wern't enabled originally.

---

### Post by Hayksk on 2010-02-10
> **warfacegod said:**
> Are you using a Touchpad or an actual mouse? If it's a mouse is it optical (laser)?

I'm using ordinary optical mouse.

---

### Post by Nunu on 2010-02-10
Do you sometimes have issues with the mouse pointer running of and doing its own thing, almost like a dirty track ball would have done?

---

### Post by warfacegod on 2010-02-10
I suppose it's *possible* for the mouse to do what you describe if you are using a plain mouse pad. Optical meeces don't like blank one color mouse pads, especially red.

---

### Post by Hayksk on 2010-02-10
> **warfacegod said:**
> I suppose it's *possible* for the mouse to do what you describe if you are using a plain mouse pad. Optical meeces don't like blank one color mouse pads, especially red.

Actually I don't use a mouse pad. I run the mouse directly on the table.
May this cause the problem?

---

### Post by warfacegod on 2010-02-10
> **Hayksk said:**
> Actually I don't use a mouse pad. I run the mouse directly on the table.
May this cause the problem?

I'm guessing your table is fairly uniform in color so yes, it's possible. Try using a newspaper or magazine cover or something to see if that helps.

---

### Post by Hayksk on 2010-02-10
> **warfacegod said:**
> I'm guessing your table is fairly uniform in color so yes, it's possible. Try using a newspaper or magazine cover or something to see if that helps.

Thanks [warfacegod]("http://ubuntuforums.org/member.php?u=537200").
I'll try it. But some time is required in order the problem to show up.

---

### Post by Nunu on 2010-02-10
> **Hayksk said:**
> Thanks [warfacegod]("http://ubuntuforums.org/member.php?u=537200").
I'll try it. But some time is required in order the problem to show up.


AHHHHH so its an intermittent problem then?:-k

---

### Post by Hayksk on 2010-02-10
> **Nunu said:**
> AHHHHH so its an intermittent problem then?:-k
  
Yes, your right.

---

### Post by Nunu on 2010-02-10
> **Hayksk said:**
> Yes, your right.

and on other OS's it works fine with no problems or inttermittant failures?

---

### Post by warfacegod on 2010-02-10
> **Nunu said:**
> AHHHHH so its an intermittent problem then?:-k

That makes even more suspicious of it being a flat color tracking issue.

---

### Post by Hayksk on 2010-02-10
> **Nunu said:**
> and on other OS's it works fine with no problems or inttermittant failures?

Right...

---

### Post by Nunu on 2010-02-10
Then I am inclined to think that there is something happening like a background process or something along those lines every now and then, that could cause this to happen. question is what, I don't think its hardware related though.

---

### Post by Hayksk on 2010-02-10
> **warfacegod said:**
> That makes even more suspicious of it being a flat color tracking issue.

I hope your right.

---

### Post by Hayksk on 2010-02-10
Is it possible that the problem is caused by any of the firefox add-ons ( especially those related to previews - e.g. "CoolPreviews" or "Tab Scope"?

---

### Post by driekus on 2010-02-18
Im having exactly the same problem here as well. It only started recently. Very confusing for me, it is intermittent. Im unsure if it is related to the problem posted here.

---

