---
title: "browser behaviour (firfox, chrome)"
date: 2011-04-01
forum: General Help
---

### Post by linux-beginner on 2011-04-01
Hi,
developing an php application on an remote server, I discovered that the application works not normal with an Ubuntu 10.10 client but in an Windows 7 client.
I open the application in firefox 3.6.16 or in Chromium 10.0.648.133, Ubuntu 10.10. I log in to the application and then make a new tab in the same browser and go to the application again in the new tab. I see that I am also logged in. After that I log out from the application in the new tab. I expect that the application is also logged out in the first tab, but this is not the case.

The application behaves as I expect on a windows 7 system in firefox and Chromium 10.
What happens in Ubuntu?
Thanx,

---

### Post by gradysghost on 2011-04-01
I think we're going to need some more information.  This likely has something to do with how you're handling session management.

To be clear, I'm going to rewrite the process as I understand it:

1. Open browser.
2. Open tab and browse to site.
3. Log in to site.
4. Open new tab in same browser.  Note that you're already logged in.
5. Log out of site in one tab.
6. Switch to other tab; you're still logged in.

If this is accurate, we need to know what happens when you refresh the page on the final remaining tab.  Does it log you out when you refresh?  How does your app handle the client side of a session?  Are you using PHP's built-in $_SESSION variable, or are you managing this through a custom cookie?  When your app handles the user's "log out" action, does it effectively remove the cookie?  What's your algorithm for doing so?  I believe the common method is to set the expiration date on the cookie to a time in the past, which forces the browser to delete the cookie.

---

### Post by linux-beginner on 2011-04-01
These are the steps:
1- open browser
2- go to the site
3- log in to the site
4- make a new tab on the same browser
5- go to the site from the new tab (already logged in)
6- log out in the new tab (this is important that the logout happens on the new tab)
7- go the the first tab (it is logged in yet, after refresh)


The behavior is others following the next test:
1- open browser
2- go to the site
3- log in to the site
4- make a new tab on the same browser
5- go to the site from the new tab (already logged in)
6- go to the first tab
7- log out 
8- go to the second tab (it is logged out after refresh)

---

### Post by gradysghost on 2011-04-01
Sounds like a problem in session management.  Did you write the code for this?  If so, can you explain to me how you're managing sessions?  Do you feel comfortable posting a link to the site so we/I can attempt to reproduce the problem?  At the very least, please explain to the best of your ability how this app handles the client side of session management.  How do you manage cookies in the browser?  This really sounds like an issue with the way the browser manages cookies.

---

### Post by linux-beginner on 2011-04-01
[PHP]
session_start ();

  // first visit
  if (!isset ($_SESSION ['id']))
  {
    $_SESSION ['id'] = session_id ();
    $_SESSION ['object'] = new AnObject ($_SESSION ['id']);
  }

  // username and password are set
  if (isset ($_POST ['username']) && isset ($_POST ['password']) &&
      $_POST ['username'] == $username && $_POST ['password'] == $password)
    $_SESSION ['object'] -> setRole (Role::ADMIN);

  // Logout
  if (InputChecker::getAction ($_GET ['actionCode']) == PageAction::LOGOUT)
    $_SESSION ['object'] -> setRole (Role::VISITOR);
[/PHP]

---

### Post by gradysghost on 2011-04-01
So this code works for a single user on a single tab in a single browser.  I'll make that assumption.

If you're already familiar with the way PHP handles session variables, skip this paragraph.  I don't want to seem condescending.  Not my intent.  Essentially, PHP creates a section of memory on the server where it can store session data, and that gets a sort of unique label.  That label is then sent to the client in the form of a cookie, so it can do a rudimentary authentication to PHP so that PHP knows which set of session variables to access per client.

I'd be interested to see if each tab is creating a new PHP session.  If so, it makes sense that logging out on one wouldn't affect the "logged in" status of the other, but it wouldn't make sense that logging out on one should result in the same effect on the other tab.

Can you run some tests to find out if opening a new tab starts a new session and gets a new session cookie from PHP?

---

### Post by linux-beginner on 2011-04-01
I know a little bit how PHP session works. I do not think that PHP makes two different sessions for two tabs (according to the same session id for both tabs).
In addition, the code works normal from a Windows 7 client. I do not understand the different reaction of the code in Ubuntu 10.10 and Windows 7.
It is also strange that logging out form second tab dose not effect the first tab, but logging out in the first tab effects the second tab.

---

### Post by gradysghost on 2011-04-01
You can test to see if it *does* create multiple sessions by monitoring the cookies, but I agree that it's unlikely.  Also the order that causes the problem is unusual.

I'm not sure what else to tell you except that it may be worth it to set up a code-based test, like a repeating AJAX request for some piece of data on the server that would be particularly telling.  Kind of like a watch on whatever piece of data the server looks at to determine the logged-in status of the client.

Good luck.  This one's a doozy.

---

