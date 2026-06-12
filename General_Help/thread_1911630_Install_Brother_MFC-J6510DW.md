---
title: "Install Brother MFC-J6510DW"
date: 2012-01-19
forum: General Help
---

### Post by aarceng on 2012-01-19
I have been to the Brother website and I am working through the steps but have got stuck on step 5.

"ia32-libs or lib32stdc++ is required to be installed."

How do I install these? 
I have looked in other posts but can't find an answer. I looked in Ubuntu Software Centre.

I tried
aarceng@aarc-desktop:~$ sudo dpkg -i --force-all ia32-libs
dpkg: error processing ia32-libs (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ia32-libs

aarceng@aarc-desktop:~$ sudo apt-get install lib32stdc++
[sudo] password for aarceng: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package lib32stdc
aarceng@aarc-desktop:~$ 


You are using Ubuntu 10.04 LTS - the Lucid Lynx - released in April 2010 and supported until April 2013.

---

### Post by plucky on 2012-01-19
> **aarceng said:**
> I have been to the Brother website and I am working through the steps but have got stuck on step 5.

"ia32-libs or lib32stdc++ is required to be installed."

How do I install these? 
I have looked in other posts but can't find an answer. I looked in Ubuntu Software Centre.

I tried
aarceng@aarc-desktop:~$ sudo dpkg -i --force-all ia32-libs
dpkg: error processing ia32-libs (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ia32-libs

aarceng@aarc-desktop:~$ sudo apt-get install lib32stdc++
[sudo] password for aarceng: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package lib32stdc
aarceng@aarc-desktop:~$ 


You are using Ubuntu 10.04 LTS - the Lucid Lynx - released in April 2010 and supported until April 2013.

Are you running the 64-bit system or the 32-bit system?

Post output from a terminal for ```
uname -a
```

If you are running a 32-bit system,you don't need to install those two libraries.

Good Luck

---

### Post by aarceng on 2012-01-20
aarceng@aarc-desktop:~$ uname -a

Linux aarc-desktop 2.6.32-37-generic #81-Ubuntu SMP Fri Dec 2 20:35:14 UTC 2011 i686 GNU/Linux


I think this means I have a 32 bit system. But I had to search the internet to work out what it meant.

[from stackoverflow]
Did you try uname -m ?

It seems like the uname -m actually gives

    * x86_64 when it is an kernel 64 bits
    * i686 for 32 bits kernel

===================
aarceng@aarc-desktop:~$ getconf LONG_BIT
32

that confirms it!

---

### Post by aarceng on 2012-01-20
Next problem; trying to install drivers

aarceng@aarc-desktop:~$ dpkg -i --force-all mfcj6510dwcupswrapper-1.1.1-1.i386.deb
**dpkg: operation requires read/write access to dpkg status area**

What does it mean and how do I fix it? :confused:

---

### Post by kurt18947 on 2012-01-20
If you haven't solved your ia32-libs problem, they're in the repositories.  I question whether you need the ia32 stuff if you're running a 32 bit system.  As I understand it (and I'm not expert)  that file enables 64 bit systems to use 32 bit drivers which Brother's printer drivers are, there are no 64 bit printer drivers from Brother AFAIK.  There are 64 bit scanner drivers though.  Why scanner drivers but not printer drivers?  I have no idea, maybe Brother feels the effort involved in creating 64 bit printer drivers is not worthwhile.  I thought that step 5 referenced is for 64 bit Ubuntu/Debian.  I don't know that there's any harm in installing ia32-libs just to be safe though.

Using sudo dpkg ...... in an account with sudo privileges should work.  Brother drivers on 32 bit OSs can be installed using a GUI installer. I've done it on 32 bit 10.04 & 10.10.  I've used GDEBI - also in the repositories - or ubuntu software center.  Ubuntu software center may grouse that Brother's drivers don't meet quality standards -- I just ignore and install anyway.

---

### Post by ProorieFleera on 2012-01-20
This economic crisis gives far more shocking information everyday. That full week ended up being no various because management via Standard Engines, Frd, in addition to Chrysler stumbled within Oregon using their management and business aircraft for you to request the write about on the $700 billion Troubled Advantage Alleviation Plan.    
    
In the shameless screen of conceit and entitlement, frontrunners connected with exactly what was previously "best inside class" organizations begged for immeasureable cash because of their jar cups outstretched as you're watching US The legislature. Prior to the Big Several ever before arrived in Wa, massive received already been dedicated to AIG in addition to a number of the major loan companies in the united kingdom.    
    
During this fiscal crisis we are finding some thing all of us by no means supposed to view inside our life : damaged pledges from main companies and also govt entities using a range never regarded as probable. We have gotten to a place where also large organizations along with substantial says such as California cannot fulfill their own bills while using the connect markets.    
    
In case you are a new California home insurance consumer, your own most significant tool has become vulnerable over the financial doom and gloom -- your own Florida house.    
    
Is it possible to name an even more holy promise compared to a single a home insurance company can make to you personally when it will take your dollars along with concurs to help make sure your house?    
    
If you purchase home owners insurance policies within Fl the insurer can be ensuring anyone rapid in addition to reasonable transaction of the claim. California insurance agencies buy reinsurance that can help all of them create excellent on this assure to you personally. Reinsurance is usually backup insurance policy coverage of which insurance agencies acquire to assist defend on their own coming from big failures preceding specific quantities.    
    
Your Texas Typhoon Devastation Fund had been created so that you can guide become stable the particular Florida property insurance policies market place immediately after Natural disaster Phil induced enormous amounts with injury to Florida with 1992. By supplying reinsurance with very affordable premiums, this account assisted to create homeowners insurance policies accessible and reasonably priced for several years.    
    
That every transformed following your Fl hurricanes connected with 2004 as well as 2005 any time Fl residence insurance policies grew to be too costly and also difficult to get once again.    
    
The particular California legislature taken care of immediately the actual California house insurance policies crisis by means of voting in 2007 in order to grow the particular reinsurance sold with the Feline Deposit by means of $12 million -- rearing the overall danger into a entire connected with $28 billion. Florida property insurance companies were forced to invest in that additional reinsurance from the talk about and also to transfer the particular cost savings came to the realization upon reinsurance to help homeowners.    
    
Like a Fl homeowner, an individual did not receive the price reductions that it legislation ended up being likely to offer. People did not have the 24% regular fee savings that have been forecast once the legislation passed. And also to help to make issues more serious, your Florida Kitty Pay for needed on an further $12 million throughout threat.    
    
Currently the California Accident Fund has told us all the frosty bond promotes will not a good supplier to get the income it needs to meet up with it's responsibilities towards insurance agencies after having a significant Texas hurricane. That recently approximated so it could spend $13 million in the future one year -- That's $15 billion a lot less than the $28 million it can be about the connect to pay!    
    
Precisely what will this indicate for your requirements to be a Sarasota property insurance plan customer?    
    
You failed to have the fee comfort people expected whilst your express got in debt it does not have any expect involving having to pay.    
    
You're at an increased risk when Fl experiences an important hurricane yearly calendar year. After the deficits of the Florida home insurance firm go over specific ranges, your business will probably inquire the particular Texas Cat Deposit to be able to repay them so that you can pay out your claim. Because the California Feline Pay for is short upon funds, you may have a long wait throughout helping your claim paid.    
    
Your assurance to repay your current Florida home insurance policies claim has not been recently much more in danger compared to it can be currently.    
    
Currently you are sure of how the Sarasota Feline Pay for cannot meet it is requirements, we should go through the thought of the Country wide Natural disaster Catastrophe Fund in which some inside California are actually driving with Washington [tyres](http://loveandrespect.com/member/28956/)  for many years. This specific Countrywide Kitten account would certainly present an extra level associated with loss security far beyond your responsibilities of the Sarasota Pet Account.    
    
The theory is actually which a Nationwide Problem Account could well be funded in part by insurance premiums paid out by policyholders with says which have been part of the account. A new Nation's Cat [tyres for sale](http://www.permaculture.org/nm/index.php/member/68749/)  Account would have been a individual finance that would gain curiosity in addition to mature through the a long time when right now there usually are not almost any promises.    
    
Fans claim that no taxpayer dollars can be was required to sustain a Country wide Pet Fund. Heritage conveys to us all generally there could be thunder storms therefore [tyres and wheels](http://biologos.org/member/7560)  large of which federal government place a burden on bucks would have to supply to cover main failures.    
    
In addition to everyone should know of which the us government cannot maintain its finances individual. Simply inquire a person inside Oregon to demonstrate anyone this massive which might be supposed to be [tyres direct](http://www.donnabalsan.com/index.php/member/31828/)  in the Social Security Confidence Finance. You'll not be found any kind of income - a bathroom drawer rich in T-Bills and also IOU's.    
    
Given that the Huge Three Auto makers and also other shameless Bundle 500 companies possess defeated Sarasota towards the strike in Oregon, it is extremely not likely [tyres and wheels](http://forums.realmacsoftware.com/index.php/member/254212/)  that the Nation's Quake Problem Account will certainly complete anytime shortly. Actually President Opt Obama can timid faraway from any additional national requirements as he people the many red printer in Oregon right now. And so do not check out the federal government to generate excellent within the assure that's made to fork out ones Texas household insurance plan maintain.    
    
Last but not least, Folks Home Insurance policy Company features regularly noted so it does not have at any place on the money it needs to spend this practically 1 / 2 the trillion [tyres cheap](http://www.pitching.com/member/265472/)  us dollars inside storm coverage it from important Texas natural disaster.    
    
A huge storm will mean which Citizens are unable to fork out also its primary obligations - those that [tyres direct](http://www.permaculture.org/nm/index.php/member/68749/)  it should spend possibly just before losses get to amounts where by Texas Storm Catastrophe Pay for reinsurance leg techinques with. And as the policyholder with Individuals, you're governed by having to pay higher specific assessments [tyres](http://uppingtheanti.org/member/39477/)  after a significant Fl storm than policyholders who've non-public home owners insurance policy : specific expenses tacked on your yearly insurance invoice.    
    
On this new fearless globe in which actually government authorities are unable to maintain the pledges here are some actions you need to get to be a California property insurance client at the moment:    
    
Get yourself a Texas breeze examination performed [tyres direct](http://www.collegescholarshipsusa.com/member/27906)  and solidify your house if you can ,.    
    
Avoid Residents Insurance plan Texas when you can.    
    
Look for a residence insurance carrier that's powerful in financial terms the other that has propagate its danger around the two Fl along with other says. A lesser number of policyholders means quicker check of the assert.    
    
Report the insurance plan declare the identical time since the California typhoon. This can help it become more inclined you will get paid out ahead of ones insurer seems towards California Kitten fund intended for refund.    
    
Last but not least. The truth that this California Feline Account can be short in income is not dropped upon Fl home insurance carriers. They may be becoming incurred regarding reinsurance by means of the organization that has openly [tyres for sale](http://www.legsonthewall.com.au/index.php/member/49950/)  stated who's are not able to fulfill the commitments. Meaning insurance companies are not having exactly what that they taken care of.    
    
You need to count on Texas residence insurance firms in order to acquire much more of their reinsurance within the private marketplace and not from the Condition involving Texas during the past year. And they're going to look for complete which cost by way of anyone by means of larger insurance rates. As long as they do not get the particular pace boosts needed, your Fl house insurance coverage may be terminated.    
    
Because Fl home insurance policies crisis persists, it's got never already been much more critical that you be on top of your Sarasota residence insurance current market regarding personal insurance. Create recognize whenever it's likely you have to find a completely new Fl residence insurance carrier.

---

### Post by ProorieFleera on 2012-01-20
An accumulation of success tips that we possess gathered more than decades of working with impartial web based business entrepreneurs. I've got designed a listing of our 100 favourites that we personally adhere to to push onward the online home business. When i tidied the actual suggestions straight into locations addressing frame of mind along with control, focus along with visualisation, occasion and process supervision, revenue along with way of living, information and knowledge, particular development and way of life, analyzing your current exercise, in addition to providing in addition to putting [tyres](http://www.thenewsliteracyproject.org/member/36848/)  value.    
    
MIND-SET & DISCIPLINE    
    
1. Be prolonged and provide by yourself time intended for energy in order to start working.    
    
3. Make up inside figures everything you don't have in knowledge.    
    
3. Observe achievement from each step.    
    
5. Figure out how to take care of the particular thoughts - everybody features a directly to have got a single - in no way allow it to be personalized.    
    
5. You are not the actual message, you're the actual messenger.    
    
6. Your friends and relations would possibly not fully grasp the voyage you're upon.    
    
7. Everything is effective if we do the job.    
    
8. In case you receive stressed along with baffled, [tyre shopper](http://whatdoyouconsiderlethal.com/member/349606/)  get back on performing basic principles.    
    
9. Complete your three-part test -- loyalty, perform behavior, consistency.    
    
10. Have a enthusiast soul. Arranged targets as well as get it done every day.    
    
11. Make a determination for you to almost any new activity. Making it with anything is about using not really making a decision.    
    
12. Being successful is usually the opportunity to carry on along with your program extended after the feelings in addition to instances encompassing ones authentic conclusion has [tyres online](http://www.childrennow.org/index.php/member/1430/)  transferred.    
    
13. The self confidence can be why is a person appealing on the market location. People invest in individuals these people know, like as well as believe in.    
    
fourteen. Prevent unfavorable contemplating in addition to unfavorable people that provide you with decrease and also steal ones ambitions.    
    
15. DREAD can be Bogus Facts Listed Genuine. Have the anxiety and undertake it regardless. Development comes from walking [tyre shopper](http://www.amandaripley.com/member/10915/)  outside your comfort zone.    
    
04. Go to your current doubts. The place where your current ideal anxieties dwell is usually the place where ones best progress is placed. (The boy wonder Sharma)    
    
teen. A good oz connected with actions is worth lots of ebooks.    
    
eighteen. Many excuses are generally equal and also undertake and don't depend.    
    
CONCENTRATE & VISUALISATION    
    
21. Understand what you want, why you need the item, in addition to if you want the item simply by. Compose that down, examine the item 2 times each day. Understand the retail price in addition to spend the price.    
    
20. Imagine your own fate -- 'see it' as well as prepare this - end up being extremely specific about what success seems as if [tyres](http://www.emarketing101.ca/member/30714/)  and appears like, as well as try this intended for every motorola milestone or goal people established.    
    
21. If you feel you are able to as well as think you cannot, a person are invariably appropriate. (Holly Honda)    
    
twenty-two. Act as solution centered.    
    
3. Fully grasp the real electric power connected with desires and goals, they will work like magnets tugging us forward and also need to be robust plenty of to help bust clear of days gone by yanking your current again.    
    
twenty four. Solely an idea gets the capacity to distributed.    
    
twenty-five. The thing you should rely on is your own operate ethic and also just how badly you want to succeed.    
    
26. Keep the inner relationship using particular growth and getting mixed up in local community.    
    
twenty-seven. Employ constructive language. Phrases, views, behavior, benefits. Do your complete challenges along with obstructions that has a constructive psychological perspective.    
    
twenty-eight. Mental visualisation can be almost all crucial to the long term success. Exactly how you would like to discover by yourself, [tyres for sale](http://www.oldguysrule.com/ee/index.php/member/60580/)  how you store your self, the objectives : produce a thorough set of photographs connected with who you intend to end up being.    
    
MOMENT & PROCESS ADMINISTRATION    
    
twenty nine. Acquire tidied.    
    
30. Consistency is greater as opposed to infrequent blitz.    
    
31. Develop a regular method of operations, control by yourself and become responsible to help on your own.    
    
thirty two. Almost everything functions -but discover a every day means of functioning of which is effective for you personally, around your individual circumstances and also obligations.    
    
thirty-three. Fill up your time and efforts just with effective activities.    
    
thirty four. Arranged the focuses on in addition to perform in reverse consequently you know what has to have completed.    
    
35. [tyres](http://chicksandbalances.com/index.php/member/23325/)  Build a sense connected with urgency and get into enormous actions.    
    
thirty seven. Bear in mind people, of all people, are worthy of your current undivided focus.    
    
thirty seven. Any person or maybe anything that attempts to help distract an individual from your objective and targets should not be tolerated.    
    
38. Getting hectic is actually not equivalent to staying successful. Don't be occupied currently being weak, be hectic introducing importance to your lifestyle.    
    
39. Build good moment operations. It isn't really the particular several hours anyone placed into your organization, it does not take company anyone place into ones hrs.    
    
45. Guide move would be the source of your current impetus and also profits development. Will not over-worry upon conversions before you [tyres and wheels](http://www.horseraceinsider.com/member/90528/)  get good direct move into your company.    
    
41. Support in addition to promote ones team members, nevertheless will not lead to someone else's business. Equilibrium motivating and also guiding using pushing independence.    
    
CASH FLOW & WAY OF LIFE    
    
38. Operate your organization, don't allow the idea operate an individual. Create a organization on the imaginative and prescient vision of the life you wish to are living and initiate located the idea.    
    
43. Progress rapidly, huge action compatible substantial results.    
    
46. Bear in mind offering any 6 determine earnings opportunity isn't really around the dollars, it's with regards to a aspiration life style free from financial debt free to operate when you'd like, in which you would like, the method that you would like    
    
1 out of 3. Just market place merchandise that will enable you to get significant return on your investment of their time in addition to price range.    
    
46. "Top Tier" Chances Bring in "Top Tier" Folks that Are generally Cleverer (And even more [tyres for sale](http://www.eeci2009.com/member/10263/)  Enjoyment To use)    
    
47. Distinguish the top five issues you do as part of your enterprise that create 80% on the results.    
    
24. Learn your business numbers -- your own working expenses along with your financial well being.    
    
forty nine. Reinvest your earnings into your advertising.    
    
50. Promote, advertise, showcase : proactive approach, help make gives, produce need.    
    
1951. Concentrate on the particular long-term continuing earnings possible not really the short-term earnings of your company.    
    
52.. Prevent discounting. People never invest in in price tag, they will invest in upon importance.    
    
53. 80% of the globe will just what everyone else does and cause a common, regular existence. Just 3% dwell remarkable life given that they create remarkable selections and also complete incredible items.    
    
54. You are the person of which sets the speed of this business. Make a decision on just what exactly your ambitions are generally as well as create your every day self-control to attain these people.    
    
KNOWLEDGE & ABILITY    
    
second there’s 55. Understand your current create and stay experienced, fully commited, loyal along with considering products you choose to market along with the firm.    
    
56. Maintain it simple, don't reinvent a successful method.    
    
57. If you find trapped, find ways to get out from the glue quickly to prevent damaging impact.    
    
58. Don't believe in what you know, become interested in learning issues you won't still learn.    
    
fifty nine. When you have issues, find out more about your small business, your solutions, your small business, your current build.    
    
58. Safer to personally do something about the knowledge found in 2 beneficial books when compared with to be able to offer from a 100.    
    
sixty one. Create your online business as you build a drinking water send. You will need [tyres and wheels](http://www.ago.state.ms.us/index.php/member/4525/)  time to build and you will need to turn the particular manage, then again the water is sold with simply a gentle touch.    
    
62. Marketing is just not a defined scientific discipline. It will require trial & miscalculation.    
    
PERSONAL DEVELOPMENT & AUTHORITY    
    
63. Compete with on your own. Complete on a monthly basis more powerful as opposed to a single previous to so that you feel to see you happen to be expanding.    
    
sixty-four. Create rely on as well as assurance inside your local community and with your current crowd.    
    
65. Certainly be a chief. Stage up to the mark : get into gear, dress up and also make an appearance and allow returning.    
    
66. Don't overlook prospects to see remarkable issues. Head out this 'extra' kilometer.    
    
67. Command is often a alternative not really a concept. Get 100% obligation. Blaim is usually deplete, by no means grumble. You might have complete control above ones upcoming.    
    
68. Train just whatever you accomplish. Folks perform what you can't that which you say.    
    
69. Accumulate stories for your merchandise, the group, a person. A recommendation is usually a legitimate account grouped together in a very highly effective means so that you can effect along with effect other people.    
    
seventy. Move out via driving your personal computer at times. Shoot movies external as well as move perform a few real world marketing    
    
71. Build a positive 'can-do' 'will-do' mind-set fuelled from your need to do well.    
    
72. Affirm the perception inside on your own, each day commemorate ones accomplishments and innovations.    
    
73. Learn in addition to embrace exactly what productive men and women do. [tyres online](http://www.childrennow.org/index.php/member/1430/)  Grasp basic principles which are doing work before you decide to alter, conform in addition to innovate.    
    
74. Accomplish this uneasy or perhaps complicated goods primary : ("Eat That will Frog", Brian Tracy). That rapidly gets secure as well as second dynamics.    
    
seventy-five. Collection a mission as a uniform, certainly not your money can buy however for the person you may turn into (John Rohn)    
    
76. Create the most effective associated with what we get nevertheless continually be eager intended for more.    
    
EVALUATING THE EXERCISE    
    
seventy seven. Study on what exactly is not working and turn a difficulty solver.    
    
81. Keep your confidence with the door.    
    
seventy nine. Examine ones placement : are your own prospects precise, accomplish that they change effectively.    
    
eighty. Prepare, Carry out, Evaluation. Tend not to put things off, simply just obtain stuck in as well as get it done. Ready, flames, purpose.    
    
seventy eight. Never turn to this magic pill -- multi-task, hunt for fresh chances, make sure perfect.    
    
82. Monitor the results in opposition to your own approach. Do you do the game?    
    
83. Meet the criteria your current prospects. Will not sell all of them, make it possible for these individuals market people. Questions include the remedy.    
    
84. Ones answers are the comments. Guilt no-one but on your own. That you are what your location is along with the way you are as a result of choices you have made as time passes.    
    
85. Should you be performing the game, receiving the figures, you are energy along with attitude is usually right, this it really is normally something lost from your experience. Conversation.    
    
90. If you don't satisfy ones targets with any one evening, will not fall the actual ball yet do the job twice as difficult the following. Don't become accustomed to taking falling the particular soccer ball. Get into gear down the road somewhat greater.    
    
87. It really is better to accomplish the project when compared with manage the actual frustration with yourself regarding definitely not assembly your current targets.    
    
GIVING & INCORPORATING IMPORTANCE    
    
88. Develop uniqueness & price throughout that which you create on the internet.    
    
90. The market industry will not spend anyone on things you need, this pays about importance. People who guide essentially the most people take advantage funds.    
    
90. In order to double your revenue, you must dual your own importance available in the market position.    
    
91. Halt so that it is about anyone, your small business, as well as things to come about. [tyres](http://www.northrupkingbuilding.com/member/33635/)  Rather identify what some others require nearly all as well as the best way to support some others get more regarding what they want.    
    
95. Consentrate on taking folks to a higher part of your sales & marketing and advertising launch, not all the way a single step.    
    
93. Authenticity drastically increases your current final results.    
    
94. Acquire the unit to get in touch with all your qualified prospects, brand-new users along with clients.    
    
92. Type groups in addition to communities to a target attention in addition to build relationships (Twitting, Myspace, Myspace, LinkedIn)    
    
ninety-six. Discover ways to show your transition along with men and women. Acquire mental learning ability. Locate his or her soreness items and also demonstrate to them the most effective and acquire all of them pondering in a very brand new route.    
    
ninety-seven. Locate men and women, sponsor these people, assist these phones preserve these people.    
    
98. Always be crystal clear regarding your business functions, how to handle it on every single stage so that you can consider other people through that procedure, cause by means of instance.    
    
99. Show, verify, recognize and invigorate your own team.    
    
100. Seek ideas, yet daily likewise become an individual else' motivation, it will eventually think awesome!

---

### Post by plucky on 2012-01-21
> **aarceng said:**
> Next problem; trying to install drivers

aarceng@aarc-desktop:~$ dpkg -i --force-all mfcj6510dwcupswrapper-1.1.1-1.i386.deb
**dpkg: operation requires read/write access to dpkg status area**

What does it mean and how do I fix it? :confused:

Try ```
sudo dpkg -i --force-all mfcj6510dwcupswrapper-1.1.1-1.i386.deb
``` as you are changing system files you need privileges.

Good luck

---

### Post by aarceng on 2012-01-25
[Some of this will probably be blindingly obvious to experienced users]
OK I have now figured out that mfcj6710dwlpr should be installed first. I also figured out I have to add the path to where the files are. 

[INDENT]aarceng@aarc-desktop:~$ sudo dpkg -i --force-all /home/aarceng/Desktop/FireFoxDownloads/mfcj6710dwlpr-1.1.1-1.i386.deb
Selecting previously deselected package mfcj6710dwlpr.
(Reading database ... 562596 files and directories currently installed.)
Unpacking mfcj6710dwlpr (from .../mfcj6710dwlpr-1.1.1-1.i386.deb) ...
Setting up mfcj6710dwlpr (1.1.1-1) ...

aarceng@aarc-desktop:~$ sudo dpkg -i --force-all /home/aarceng/Desktop/FireFoxDownloads/mfcj6510dwcupswrapper-1.1.1-1.i386.deb
(Reading database ... 562622 files and directories currently installed.)
Preparing to replace mfcj6510dwcupswrapper 1.1.1-1 (using .../mfcj6510dwcupswrapper-1.1.1-1.i386.deb) ...
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
Unpacking replacement mfcj6510dwcupswrapper ...
dpkg: mfcj6510dwcupswrapper: dependency problems, but configuring anyway as you requested:
 mfcj6510dwcupswrapper depends on mfcj6510dwlpr; however:
  Package mfcj6510dwlpr is not installed.
Setting up mfcj6510dwcupswrapper (1.1.1-1) ...
[B][COLOR="Red"]ERROR : Brother LPD filter is not installed.
chmod: cannot access `/etc/opt/brother/Printers/mfcj6510dw/inf/brmfcj6510dwrc': No such file or directory
chmod: cannot access `/etc/opt/brother/Printers/mfcj6510dw/inf': No such file or directory[/COLOR][/B]
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 

aarceng@aarc-desktop:~$ [/INDENT]

Now what do I do about this? (besides switching to Windows)

---

### Post by plucky on 2012-01-26
> sudo dpkg -i --force-all /home/aarceng/Desktop/FireFoxDownloads/mfcj6710dwlpr-1.1.1-1.i386.deb
Selecting previously deselected package mfcj6710dwlpr.
(Reading database ... 562596 files and directories currently installed.)
Unpacking [color=red]mfcj6710dwlpr[/color] (from .../mfcj6710dwlpr-1.1.1-1.i386.deb) ...
Setting up mfcj6710dwlpr (1.1.1-1) ...


Could it be that you didn't install the correct lpr driver?

Please post output of ```
dpkg -l | grep -i brother
```

Good luck

---

### Post by aarceng on 2012-01-28
Thank you Plucky. Yes I had installed the incorrect driver.

aarceng@aarc-desktop:~$ dpkg -l | grep Brother
ii  mfcj6510dwcupswrapper                      1.1.1-1                                         Brother CUPS Inkjet Printer Definitions
ii  mfcj6510dwlpr                              1.1.1-1                                         Brother lpr Inkjet Printer Definitions

The printer is now working.:guitar:

---

### Post by detritusuk on 2012-03-25
Thanks folks.  Your post helped me resolve an issue I was having using a network printer with ubuntu 11.04.

Brother's website explanation of what to do is terrible.

This resolved it.

Many Thanks

Stephen

---

