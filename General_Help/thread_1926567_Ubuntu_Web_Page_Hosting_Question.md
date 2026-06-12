---
title: "Ubuntu Web Page Hosting Question"
date: 2012-02-16
forum: General Help
---

### Post by ryanparmstrong on 2012-02-16
Howdy guys,

I had a question involving hosting a webpage using the BeagleBoard xM with Ubuntu.

Currently, we have the device running a Glade GUI (.glade extension) that is performing the functionality of a thermostat.  We also have Apache installed and I have configured a basic Apache web-server using my laptop and Ubuntu.  What we would like to do is have the GUI be accessible via the internet through an Apache web-server running on the BeagleBoard xM.

The first question would be, is it possible to run the same GUI in a Apache web-server as well as running it as an application on the BeagleBoard xM?

The second question:  Is it possible to put a Glade GUI directly onto an Apache web-server, or does it require some manipulation.  If it does require manipulation, is there a guide on how to do this?

---

### Post by ryanparmstrong on 2012-02-16
A quick update, we will be running the GUI on a separate BeagleBoard C4 with 10" touchscreen and are wanting to have this GUI also usable online via the BeagleBoard xM (Using Apache?)

Has anyone ever used GladetoHTML?  Is this a possibility?

[https://github.com/epw/gladetohtml/blob/master/README](https://github.com/epw/gladetohtml/blob/master/README)

Thanks

---

### Post by aasdfasdfg on 2012-02-16
You keep mentioning Glade: I am assuming you mean that the application uses GTK+, and you design the interfaces in Glade. Depending on whether you use GTK 2 or GTK 3, there are different options.

Probably the most exciting option is available with GTK 3; there is now (experimental) support for an HTML5 backend. Please see [here]("http://www.webupd8.org/2011/09/gtk-32-released-with-html5-allows.html") for more information.

What language is your theromstat program written in (GTK has bindings in a variety of languages). This information would affect your options for porting your app manually to run in a browser.

---

### Post by ryanparmstrong on 2012-02-17
That is correct, we are using GTK libraries and the Glade interface designer.

Our software guy is using GTK3.

The back-end is all written in C.

What would you suggest for our team?

---

### Post by aasdfasdfg on 2012-02-18
The current HTML5 backend for GTK can be enabled by compiling GTK with the following flags:
--enable-x11-backend --enable-broadway-backend 
These should be passed into the ./configure script.

[This]("http://developer.gnome.org/gtk3/3.3/gtk-building.html") is the official reference for building GTK.

For full functionality, the client needs to run a browser that supports Websockets.

---

### Post by ryanparmstrong on 2012-02-19
If we do end up using the HTML5 functionality of GTK 3.2, will we still be able to access the USB ports in the converted HTML GUI?  

As this is a thermostat, we will need to receive temperature reading updates from a host of pic based sensors, that use Xbee devices connected via USB, and pass those into the GUI.  Will the program automatically take care of this?

Thanks

---

