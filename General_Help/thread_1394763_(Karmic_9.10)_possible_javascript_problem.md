---
title: "(Karmic 9.10) possible javascript problem"
date: 2010-01-31
forum: General Help
---

### Post by syrel on 2010-01-31
I am stumped here so maybe someone has a suggestion.  I cant seem to view youtube videos as it says either Javascript is not enabled or flash is not installed. 

First off I know both are not true.  At first I thought it was a flash video, but I ran into a blog today that had an embedded flash vid and it played fine, yet youtube still complained.  yet if i go to the Adobe test site <http://www.adobe.com/software/flash/about/>, the flash video does not play.

  then i used a proxy site to browse youtube and the videos played just fine. i disabled all plugins and then uninstalled all plugins and add-ons.  no change.  i've tried disabling and enabling javascript but no change. 
 

I then noticed that I couldnt use the Adobe download site because the javascript it uses was not working.  given that, I thought maybe javascript is jacked.   i found some test sites and got varied results, but most sites tell me JS is working.
<http://www2.webkit.org/perf/sunspider-0.9/sunspider-driver.html> just hangs and does nothing, but it works fine on XP.  
<http://niuonline.niu.edu/browsertest.html> does nothing
<http://www.cyscape.com/showbrow.aspx?bhcp=1> loops endlessly
<http://jsbenchmark.celtickane.com/Run.aspx#> does nothing
<http://v8.googlecode.com/svn/data/benchmarks/v5/run.html> does nothing
<http://www.b2knet.com/> says JS is not enabled in FF, but when using Chromium it says the opposite
<http://ce.byu.edu/is/share/help/scriptTest.htm> test is successful, the text is visible and moving
<http://www.dancesoft.com/browsertest.htm> everything passed
<http://www.adspeed.com/Knowledges/262/Problems_with_Account/howto_test_browser_supports_JavaScript.html> passed the test
<http://jdstiles.com/java/brotest.html> my fav, most tests passed, but a few did fail.  browsers do not support some of the functions like clip object, etc. 
<amazon.com> the main side menu does not respond. neither does the JS menu at <newegg.com>

I've tried 5 different browsers (FF, Seamonkey, Arora, Chromium, and Dooble) all the results are identical.   I've also tried reinstalling a browser or two, as well as creating a new profile, but no luck.  then I noticed I couldnt login to Facebook or myspace and I realized that they both use a LOT of javascript.  

i tried installing and uninstalling the NoScript add-on just incase but that didnt do anything.  i've installed the restricted extras package and disabled my firewall.   i've also tried reinstalling the 9.10 OS from scratch and going straight to install flash and try it then, but it still didnt work.  the only thing currently installed on FF is the ubuntu FF mods v0.8, which I cant uninstall because it just reinstalls it automatically.  that aside, all the other browsers have the same problem anyway. 

I dont know what else to try.  I've googled the hell out of this but havent found anything.  Any real suggestions would be appreciated. :)

---

