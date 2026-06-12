---
title: "Which 32-bit library to install and from where?"
date: 2009-10-07
forum: General Help
---

### Post by cmnorton on 2009-10-07
I would like to get a program to compile and link properly on Ubuntu 9.04.
This is a 32-bit library problem.

This command line:

```

gcc -m32 -lncurses x.c

```produces these errors:

```

/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.3/../../../libncurses
.so when searching for -lncurses
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.3/../../../libncurses
.a when searching for -lncurses
/usr/bin/ld: skipping incompatible /usr/lib/libncurses.so when searching for -lncurses
/usr/bin/ld: skipping incompatible /usr/lib/libncurses.a when searching for -lncurses
/usr/bin/ld: cannot find -lncurses
collect2: ld returned 1 exit status

```What library do I need to build? Obviously, I believe it's libncurses, but I need to know which one and where to get it.

I have listed the program source code for x.c below.
Any pointers would be appreciated.
Thank You.
```

#include <time.h>
#include <curses.h>

int current_getch;
int doloop = 1;
static WINDOW *mainwnd;
static WINDOW *screen;
WINDOW *my_win;

int now_sec, now_min, now_hour, now_day, now_wday, now_month, now_year;
time_t now;
struct tm *now_tm;

void screen_init(void) {
mainwnd = initscr();
noecho();
cbreak();
nodelay(mainwnd, TRUE);
refresh(); // 1)
wrefresh(mainwnd);
screen = newwin(13, 27, 1, 1);
box(screen, ACS_VLINE, ACS_HLINE);
}

static void update_display(void) {
curs_set(0);
mvwprintw(screen,1,1,"-------- HEADER --------");
mvwprintw(screen,3,6,"TIME: %d:%d:%d", now_hour, now_min, now_sec);
mvwprintw(screen,5,6,"DATE: %d-%d-%d", now_day, now_month, now_year);
mvwprintw(screen,7,6,"PRESS q TO END");
mvwprintw(screen,10,1,"-------- FOOTER --------");
wrefresh(screen);
refresh();
}

void screen_end(void) {
endwin();
}

void maketime(void) {
// Get the current date/time
now = time (NULL);
now_tm = localtime (&now);
now_sec = now_tm->tm_sec;
now_min = now_tm->tm_min;
now_hour = now_tm->tm_hour;
now_day = now_tm->tm_mday;
now_wday = now_tm->tm_wday;
now_month = now_tm->tm_mon + 1;
now_year = now_tm->tm_year + 1900;
}

int main(void) {
screen_init();
while (doloop) {
current_getch = getch();
if (current_getch == 113) {
doloop = 0;
}
maketime();
update_display();
sleep(1);
}
screen_end();
printf("TEST ENDS\n");
return 0;
}

```

---

### Post by cmnorton on 2009-10-18
This was resolved by modifying the order of a ld path and by getting proper installation order from Informix.

---

