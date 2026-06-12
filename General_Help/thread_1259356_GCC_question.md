---
title: "GCC question"
date: 2009-09-06
forum: General Help
---

### Post by jingpro on 2009-09-06
Hello,

I am learning STL using G++ under Ubuntu. Today I copied following C++ code from a text book (Absolute C++) and tried to run it:

[PHP]#include <iostream>
#include <vector>
using std::cout;
using std::endl;
using std::vector;
using std::vector<int>::iterator;

int main()
{
	vector<int> container;
	for (int i=1;i<=4;i++)
		container.push_back(i);
		
	cout << "Here is what is in the container:\n";
	iterator p;
	for (p=container.begin();p!=container.end();p++)
		cout << *p << " ";
	cout << endl;
}
[/PHP]
When I compile it, got following error:

STL_vector.cpp:6: error: ‘std::vector<int, std::allocator<int> >’ is not a namespace

So, what's the problem of:  using std::vector<int>::iterator;  

Sorry for this kind of newbie question. Thanks in advance for your help.

regards,
Derek

---

### Post by cyberfish on 2009-09-06
[http://cboard.cprogramming.com/cplusplus-programming/119297-newbie-question-about-stl-under-gcc.html](http://cboard.cprogramming.com/cplusplus-programming/119297-newbie-question-about-stl-under-gcc.html)

---

### Post by jingpro on 2009-09-06
This post was posted on other 10+ forums (I copied, copied, copied .......). Can you spend time to locate them and put links here? If you can do so, I give you candy :D

---

### Post by Daemn on 2009-09-06
> **jingpro said:**
> This post was posted on other 10+ forums (I copied, copied, copied .......). Can you spend time to locate them and put links here? If you can do so, I give you candy :D

Haha.. you're an a-s-s. At least edit your other topics since you've already gotten your answer. So you don't waste anyone elses time. You shouldn't post on more than 1 forum unless you haven't gotten any responses within a few hours and you're desperate. This question wasn't even worth a topic.

Google only showing 3 so far:
#1 - [http://ubuntuforums.org/showthread.php?p=7906034](http://ubuntuforums.org/showthread.php?p=7906034)
#2 - [http://cboard.cprogramming.com/cplusplus-programming/119297-newbie-question-about-stl-under-gcc.html](http://cboard.cprogramming.com/cplusplus-programming/119297-newbie-question-about-stl-under-gcc.html)
#3 - [http://www.codeguru.com/forum/showthread.php?threadid=484125](http://www.codeguru.com/forum/showthread.php?threadid=484125)

---

### Post by jingpro on 2009-09-06
google is not so powful as you imagined. At least, I am happy someone really spend time to google the number of post. Life is really so boring for you?

---

### Post by Daemn on 2009-09-06
> **jingpro said:**
> google is not so powful as you imagined. At least, I am happy someone really spend time to google the number of post. Life is really so boring for you?
 
Coming from the guy who posted 10 times without even waiting for an answer. Googling isn't hard. Neither is your question. Inbetween coding I monitor the forums to help people who actually need it. Isn't that what you expected when you posted? Keep **insulting** (people who browse these forums involved in the topics) and/or **abusing** (spamming your topic everywhere) the people trying to help. Good stuff.

---

### Post by jingpro on 2009-09-06
Hi Daemn,

Why you said my post is not worthy (just because it is a newbie question as I put in the title)? This is technical forum, everyone has the right to ask his question.

I know my question is too simple, but were you a guru when you were born? Everyone has a learning curve. You may be a guru, at least compared with me. But this is just C++. But I am sure I am a master in lots areas compared with you. 

I really hate those kind of arrogant guys on internet forum. They are arrogant on net, but may be looser in real life.

It is bad to post multiple times in one forum, but Why I can not post my question in more than one forums? If I want to buy something, I can go to different shops, and get different information.  

If my post waste someone's time, only those guys who wanders all around (visit multiple forums simultaneously) on the internet. People do not have worthy works in real world may do this virtual walking on the net. 

If I waste yout time, it is like that I wasted time on a staff who simultaneously works in multiple shops. 

Finally, sorry I wasted your time, internet walker. But, If I did not, you are still wasting your time on internet,...just walking.

BTW, I teased you. I just posted 3 times. If I posted 10 times, you would be too tired to walk so far away.....u r lucky, poor guy.

---

### Post by Daemn on 2009-09-07
By posting on multiple forums you aren't wasting my time, [jingpro]("http://ubuntuforums.org/member.php?u=578040"), you are wasting other people's time who read and answer your question.. because you already have the answer on a different forum (and they don't know about it). So they spend their time trying to help you, thinking you need help, when they don't even know you already got your answer on a different forum.

How can you not understand this?

Anyway, just because I know how to use the internet or code better than yourself, doesn't have any baring on who I am in real life (loser, cool, or otherwise). The same goes for yourself.

It's not arrogance, it's anger. I'm not even close to a guru (got about 7 more years at least).

---

### Post by miklcct on 2009-09-11
It's simple, GCC has already told you the problem. The program **itself** is ill-formed.

---

