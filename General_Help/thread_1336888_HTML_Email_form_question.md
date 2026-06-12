---
title: "HTML Email form question"
date: 2009-11-24
forum: General Help
---

### Post by vurwolf on 2009-11-24
Hey all,

I know this doesn't have anthing to do with ubuntu but I can't find the answere to this anywhere else and I know if anyone can answere it someone here can.   OK.....I am trying to edit this form to send to whatever email I need.

Here is the code

[HTML]<form id="ContactForm" action="">
											<div class="container">
												  Enter your name:<br /><label><input type="text" value="" class="input"  onblur="if(this.value=='') this.value=''" onfocus="if(this.value =='' ) this.value=''"/></label>
												  Enter your email:<br /><label><input type="text" value="" class="input" onblur="if(this.value=='') this.value=''" onfocus="if(this.value =='' ) this.value=''" /></label>
												  Enter your fax:<br /><label><input type="text" value="" class="input" onblur="if(this.value=='') this.value=''" onfocus="if(this.value =='' ) this.value=''"/></label>
												  Enter Your Message:<br />
												  <div class="text-bg">
													<textarea cols="" rows="" onblur="if(this.value=='') this.value=''" onfocus="if(this.value =='' ) this.value=''"></textarea>
													</div>
												  <div class="alignright">
													<a class="text-link" href="#" onclick="document.getElementById('ContactForm').reset()"><span><span>Clear</span></span></a><a class="text-link" href="#" onclick="document.getElementById('ContactForm').submit()"><span><span>Send</span></span></a>
												</div>
										  </div>
										</form>	[/HTML]	

Thanks everyone

---

### Post by Bag-O-Stuff on 2009-11-25
You are missing a whole bunch of information here.  Forms like this don't work without some sort of supporting app behind it.  PHP, JSP, etc...  There's a ton of them.  This form alone will do you no good.

PHP has a built in mail command.  There are also other 3rd party apps that make the mailing a little easier or add features.  [http://swiftmailer.org/](http://swiftmailer.org/) is a pretty good one.

Check the docs on [php.net for the "mail" command]("http://us3.php.net/manual/en/function.mail.php") and it might give you a better idea on how this all works.  Or, supply some more information on what you are trying to do.

---

### Post by scouser73 on 2009-11-25
Try this: [[COLOR="Red"]**HTML Email Form**[/COLOR]]("http://www.web-source.net/html_email_form.htm")

---

### Post by akakingess on 2009-11-25
Also, just for your information, have you tried out the Developers Shed? [forums.devshed.com]("http://www.devshed.com") would be a great place for those kinds of answers just for future ref.

---

