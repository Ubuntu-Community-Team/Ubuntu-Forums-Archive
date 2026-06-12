---
title: "hscale gtk+"
date: 2010-12-17
forum: General Help
---

### Post by stealthc on 2010-12-17
working with tr-prefs.c from transmission source code.
here is the source for that page:
[https://trac.transmissionbt.com/browser/trunk/gtk/tr-prefs.c](https://trac.transmissionbt.com/browser/trunk/gtk/tr-prefs.c)

What I would like to do is add the following bit of code:
[COLOR="Blue"]static GtkWidget*
new_hscale( const char * key,
                 int          low,
                 int          high,
                 int          step,
                 gpointer     core )
{
    GtkWidget * w = gtk_hscale_new_with_range( low, high, step );
    g_object_set_data_full( G_OBJECT( w ), PREF_KEY, g_strdup( key ), g_free );
    g_signal_connect( w, "value-changed", G_CALLBACK( chosen_cb ), core );
    return w;
}[/COLOR]
AND (just above where it says "***** Peer Tab"):
[COLOR="Blue"]
/****
*****  VIRTUAL HARD DRIVE TAB
****/

static GtkWidget*
vhddPage( GObject * core )
{
    int          row = 0;
    const char * s;
    GtkWidget *  t;
    GtkWidget *  w;
    GtkWidget *  w2;

    t = hig_workarea_create( );
    hig_workarea_add_section_title( t, &row, _( "Virtual HDD" ) );

    s = _( "Set Virtual HDD Size:" );
    w = new_check_button( s, (PREF_KEY_VIRTUAL_HDD_ENABLE), core );
    w2 = new_hscale( PREF_KEY_VIRTUAL_HDD_SIZE, 1, 1000, 1, core );
    gtk_widget_set_sensitive( GTK_WIDGET( w2 ), pref_flag_get( PREF_KEY_VIRTUAL_HDD_ENABLE ) );
    g_signal_connect( w, "toggled", G_CALLBACK( target_cb ), w2 );
 
   hig_workarea_add_row_w( t, &row, w, w2, NULL );
    hig_workarea_finish( t, &row );
    return t;
}
[/COLOR]
AND (near the bottom):
[COLOR="Blue"]
    gtk_notebook_append_page( GTK_NOTEBOOK( n ),
                              vhddPage( core ),
                              gtk_label_new ( _( "Virtual HDD" ) ) );
[/COLOR]


There was no use of hscale in any of the menu dialog boxes anywhere, so this doesn't seem to work.  The form appears correct but the slider fails to remember values.  In the configuration files it shows a value of 20, but does not display on the slider, nor does using the slider update the value.  The check box works fine.

I'm new to this I figured UI would be the easiest place to start.  There is obviously a learning curve but I've been trying for hours and cannot figure out how to get this damned thing working.... :(

---

