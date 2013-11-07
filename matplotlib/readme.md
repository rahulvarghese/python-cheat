scientific plotting library

#install

altough it is available in pypi, there are tons of dependancies which pip may not
install, and it even fails silently!

therefore **don't use the pip install:

   #sudo pip install matplotlib

but use the distro's package manager. On ubuntu:

   sudo aptitude install python-matplotlib

#developping

clone besides of being able to hack matplotlib,
you also get of tons of example files with this!

if you are on Ubuntu get the built dependencies:

    sudo aptitude build-dep python-matplotlib

then build c extensions and install with:

    sudo python setup.py install

##test hacks

you cannot put the python files in your python path simply without installing,
because the compiled dependencies won't go to the correct place without an install
(crashes on `_path` not found).

So, after you made changes do again:

    sudo python setup.py install

after you build the files c files, which is what takes the longest,
you don't have to build them again, so after you hack just:

the problem with this is that you cannot keep the distro default installed also.

TODO how not to install after every change

#architecture

##state machine

not object based, but state machine based.

This means that you often have a current something, and you modify the curent something.

this methods like gca() which get you the current something.

rationale: easier to type on interactive sessions

##objects

- figure:              everything
- axes:                each subplot, including several axis
- axis (!= axes):      the line with the ticks and numbers

#show

plot to screen

    plt.plot([0,1])
    plt.show()

on window close, clears plot, so if you have to replot if you want to reuse the old plot:

    plt.plot([1,0])
    plt.show()

#savefig

plot to file

recommended formats are:

- sgv: vector. Very precise, but needs to be transformed into bits before being put in a pdf:
- png: loseless compression. Simpler to put in pdf because it represents bits directly:

examples:

    plt.plot([0,1])
    plt.savefig( 'svg.png', format='png', bbox_inches='tight' )
    plt.savefig( 'png.png', format='png', bbox_inches='tight' )

#format options

many format options can be given on either:

- in a single format string at once
- in separate kwargs

use only separate kwargs in non-interactive programs since this is more manageable

##string

    plt.plot([0,1], 'r--')
    plt.show()

##kwargs

    plt.plot([0,1,2,3], [0,1,4,9], color='r', linestyle='--'  )
    save_svg_clear('r--kwargs')