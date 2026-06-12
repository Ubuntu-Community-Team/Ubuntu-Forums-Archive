---
title: "Curses programming with python"
date: 2005-02-06
forum: General Help
---

### Post by python on 2005-02-06
I think I am being stupid here. I just started learning how to program curses in python. All this little program does is draw a smaller, new window with 'N' or 'n' and quits on 'Q' or 'q'. You have to close the smaller first, like a modal popup I suppose. Problem is, if the cursor is on the second little window, and either 'N' or 'n' is pressed, it skips back to the first and will quit out, sort of like an 'ALT+TAB' effect. What's going on!?

```
#!/usr/bin/python

def main(stdscr):
	#fixed VT100 size
	global screen
	screen=stdscr.subwin(23, 79, 0, 0)
	screen.box()
	screen.addstr(1,1,'Window 1',curses.A_REVERSE)
	screen.hline(2,1,curses.ACS_HLINE,77)
	screen.refresh()
	while 1:
		c=screen.getch()
		if c in (ord('Q'), ord('q')):
			break
		elif c in (ord('N'), ord('n')):
			screen2=stdscr.subwin(10,20,3,3)
			screen2.box()
			screen2.addstr(1,1,'Window 2',curses.A_REVERSE)
			screen2.hline(2,1,curses.ACS_HLINE,18)
			screen2.refresh()
			c2=screen2.getch()
			if c2 in (ord('Q'),ord('q')):
				screen2.erase()
				screen.refresh()
			else:
				pass
		else:
			pass

if __name__=='__main__':
	import curses, traceback
	try:
		#initialise curses
		stdscr=curses.initscr()

		#other necessary setup calls
		curses.noecho()
		curses.cbreak()

		#hide cursor
		#curses.curs_set(0)
		
		stdscr.keypad(1)
		main(stdscr)		

		#set terminal back
		stdscr.keypad(0)
		curses.echo()
		curses.nocbreak()
		curses.endwin()
	except:
		stdscr.keypad(0)
		curses.echo()
		curses.nocbreak()
		curses.endwin()
		traceback.print_exc()
```

---

### Post by python on 2005-02-06
Ah. No worries. My logic was just rubbish. Fixed it now.

---

