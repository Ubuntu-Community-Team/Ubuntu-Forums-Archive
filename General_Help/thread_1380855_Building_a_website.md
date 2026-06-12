---
title: "Building a website"
date: 2010-01-14
forum: General Help
---

### Post by marcopolo1981 on 2010-01-14
Hi gang.

I need some advice about creating a website.
Can somebody please explain what Dreamweaver CS4 can do that Kompozer can't? I currently have both, and Kompozer looks a lot easier to use, and has a simpler interface.
Are there any better software to use to create a website?

Also, anyone got any tips for a first-timer?

Much appreciated

Mark

---

### Post by john newbuntu on 2010-01-14
Dreaweaver is a commerial product and obviously for the price you pay gives you a rich set of features like instant pre-view of your website, view under different browsers, templatization, server support, code organization, xhtml checking, css support, subversion integration, editing files on your host etc.
Really speaking, you can create a webpage out of just about any of the web tools that come with linux like Quanta plus, bluefish or Kompozer.  I know they are not as feature rich as Dreamweaver.  But the real crux of the website is not in the tool you use but in the design.  For all I care, you could just use gedit with some javascript and php to create your website.  The time in such an approach might increase significantly though especially in playing with the nitty-gritty details.

Here's an old list of tools for website editing.  You could also add Amaya to this.
[http://tips.webdesign10.com/using-linux-for-web-design-and-development-ubuntu](http://tips.webdesign10.com/using-linux-for-web-design-and-development-ubuntu)

---

### Post by konqueror7 on 2010-01-14
interface plays a role in dev't, so if you go with kompozer then okay. to give you some alternatives, there are Aptana, NetBeans, and Quanta Plus to name a view. if you want to have cross-platform ide, try Netbeans, Aptana, or Dreamweaver. 

Dreamweaver may help you in later and bigger project because it got lots of functions and features.

oh, you haven't specified what language you are going to use. i assume you will be using PHP in this case, you may want to chack out [W3Schools]("http://www.w3schools.com") for web dev't tutorials and take a look at installing [LAMP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by marcopolo1981 on 2010-01-14
Thanks for your responses gents. I am still confused, so will try to better explain my situation.

We have never done anything like this before, so everything is a bit daunting.
We already have a website, but its content is very basic. It was maintained for us, so we never had to edit anything ourselves. When we asked if we could make changes ourselves, we were given a username and password in order to see the control panel, but there is nowhere for us to update the content. 
So, not understanding what to do, we joined Webstarts and created a free website there. We could edit everything and see the changes instantly, which is what we need as we have no understanding what so ever about html code and other languages.
Our new site is now complete, and we want to transfer everything over to the existing site. We was told by the old maintainer to use something like Filezilla, Kompozer, or Dreamweaver CS4 in order to do this. 
We have downloaded all the web pages and their images to our computer and can disconnect from the internet and see everything as though we were online. But what now?
How do we update our current site with the new content?
And when that is done, what would I use to then edit that content? 
I think I prefer to use Kompozer as I like the layout and appearence of simplicity, but looks can be decieving. 
As for what language we have used, I couldn't begin to guess! I supose it will be whatever Webstarts use.
So to sum it all up, how do I put my new website online? What would you use to do it? Can you give step-by-step guide in doing this, or point me in the right direction?

Hope I haven't rambled too much and you can uderstand my dilemma.

Regards
Mark

PS. I have bookmarked the links you provided, and am reading them now. If the anser to my questions are there, Thank you. I will post back if I find the solution.

---

### Post by Axess_Denied on 2010-01-14
From what it sounds like, your old maintainer is telling you that you need to move your website file (typically something like index.html) to your original server. 

Under your control panel look for something called 'file management' or similar. This is where you want to put your new site's index file and replace the old one. 

Filezilla and the like are going to serve as FTP clients to put the files on your server. You can also just go to

**Places > Connect to Server** in Ubuntu and do the same thing. Typically choose 'FTP (with login)' and get your ftp.sitename.xxx login and password from your webhost.

Hope this helps. If you need anything, post!

---

### Post by indytim on 2010-01-14
Use Filezilla or another program to transport the web site you have stored locally to the hosting service where you production web site is located.  

As far as maintenance, if you maintain your pages local to your Ubuntu ops, you can then "upload" changes to the hosting service site as I described above.

-IndyTim

---

### Post by tgalati4 on 2010-01-14
Find an old machine.
Install Ubuntu Hardy Server
Install LAMP
Install Drupal

If you already have LAMP installed, then just install Drupal:

sudo apt-get install drupal5

When you are done playing with that, get the latest drupal from drupal.org.

---

### Post by marcopolo1981 on 2010-01-15
Thanks again for your responses.

We are just waiting for the fella who maintained the old site to archive its contents and then we will be uploading the new content.
I will keep you posted

Thanks again
Mark

---

### Post by marcopolo1981 on 2010-01-19
We are live!!!!:D

Thanks everyone for your advice. We used Webstarts to create the layout and links, etc...
Then used Kompozer to tidy them up a bit, check spellings and basic stuff like that.
We tried to use the publish function in Kompozer but kept getting a 503 error, so used Filezilla to publish the pages.

Thanks again.

Mark

---

### Post by msafi on 2010-01-19
Do you think you can post the link to your site[]("http://msafi.com/software-reviews/how-to-setup-a-review-and-comparison-site-using-wordpress/%20How%20to%20Setup%20a%20Review%20and%20Comparison%20Site%20Using%20WordPress")? I would like to take a look at it

---

### Post by marcopolo1981 on 2010-02-24
> **msafi said:**
> Do you think you can post the link to your site[]("http://msafi.com/software-reviews/how-to-setup-a-review-and-comparison-site-using-wordpress/%20How%20to%20Setup%20a%20Review%20and%20Comparison%20Site%20Using%20WordPress")? I would like to take a look at it

Sorry mate. I hadn't been watching this thread.

The website we have now is [http://www.oldhallcottage.co.uk/](http://www.oldhallcottage.co.uk/)

If you have any suggestions, I will be happy to hear them!

---

