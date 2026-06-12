---
title: "Python troubles (pygtk, timer, transparency)"
date: 2011-01-09
forum: General Help
---

### Post by El_Belgicano on 2011-01-09
Hi all, I'm stuck with a widget that's not updating when it should be updating: it only refreshes on "expose_event", I'm not able to get the timer do his job, any help?

Code:```
#!/usr/bin/env python
import sys, gobject, os, gtk

class Impulse(gtk.DrawingArea):

	def __init__(self):
		gtk.DrawingArea.__init__(self)
		self.connect("expose_event", self.expose)
		os.chdir("path_to_libs_impulse")
		import impulse
		sys.modules[ __name__ ].impulse = impulse
		impulse.setSourceIndex(0)
		self.update()
		self.timer = gobject.timeout_add(100,self.update)
        
	def expose(self,widget,event):
		self.cr = widget.window.cairo_create()
		self.cr.rectangle(event.area.x, event.area.y, event.area.width, event.area.height)
		self.cr.clip()
		self.draw(self.cr)
		return False
		
	def update(self):
		return True

	def draw(self,cr):
		audio_sample_array = impulse.getSnapshot(True)
		l = len(audio_sample_array)
		rect = self.get_allocation()
		width,height = (rect.width,rect.height)
		cr.set_source_rgba(0.439,0.502,0.565,0.7)
		cr.rectangle( 0, height-2, width, 2)
		n_bars = 80
		bar_width = 5
		bar_spacing = 2
		bars_width = n_bars * (bar_width+bar_spacing) + bar_width
		moveit = (width-bars_width)/2
		for i in range( 0, l, l / n_bars ):
			bar_amp_norm = audio_sample_array[i]
			bar_height = bar_amp_norm * height * 20
			cr.rectangle(moveit+(bar_width+bar_spacing)*(i/(l/n_bars)), height-bar_height, bar_width, bar_height)
		cr.fill()
		cr.stroke()

def main():
	window = gtk.Window()
	content = Impulse()
	window.resize(800,200)
	**window.set_opacity(0)**
	window.add(content)
	window.connect("destroy", gtk.main_quit)
	window.show_all()
	gtk.main()

if __name__ == "__main__":
	main()


```

Also I'd like the background to be transparent, and **window.set_opacity(0)** is not the right function or not called well or whatever else...

I'm no programmer so the code shown is mostly a copy-paste from some examples I found on the web, I worked out some errors and made the draw function look the way I wanted it to display the data.
Yet I'm stuck at the timer and transparency.

Thanks in advance.


**Edit:** After controlling the script, it appears the update is happening, but it's not re-running the function "expose".

---

### Post by m.alaa8 on 2011-05-27
try this:
```

        while gtk.events_pending():
            gtk.main_iteration(False)
            #type here what you want to be updated example: self.wTree.get_widget('label1').set_text("refresh")

```
use gtk.gdk.Window for transparency.
visit [http://www.pygtk.org/docs/pygtk/class-gdkwindow.html](http://www.pygtk.org/docs/pygtk/class-gdkwindow.html)

---

