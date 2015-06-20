FreeBSD Port for x11-wm/i3 GAPS option
======================================

Testing the port
----------------

You can test the port by cloning this repository and enabling the ``GAPS``
option in config.

.. code-block:: sh

    git clone https://github.com/tony/i3-gaps-freebsd.git
    cd i3-gaps-freebsd

    # one way
    make WITH=gaps install clean

    # via option tui
    make config
    make install clean

This repo
---------

To preserve history and merge future versions, this project was split off 
https://github.com/freebsd/freebsd-ports on GitHub.

.. code-block:: sh
    git clone https://github.com/freebsd/freebsd-ports
    cd freebsd-ports
    git remote add i3-gaps-freebsd https://github.com/tony/i3-gaps-freebsd.git
    git subtree split -P x11-wm/i3 -b i3-gaps-freebsd
    git push i3-gaps-freebsd master:i3-gaps-freebsd

i3 repo
-------

The project repository is at https://github.com/tony/i3, which is forked from 
https://github.com/i3/i3, and includes the latest ``gaps`` and ``gaps-next`` 
branches from https://github.com/Airblader/i3.

Keep ``files/extra-patch-gaps`` in sync
----------------------------------------

Download this repository 
``git clone https://github.com/tony/i3-gaps-freebsd.git`` and ``cd`` into it.

``make extract`` to grab the normal release and place it into ``work/i3-$DISTVERSION``

When inside ``gaps``, run ``make dist``, and ``tar xvf`` the generated 
``i3_*.tar.bz2`` and ``cd`` into it.

Then ``diff -N -r -u i3-gaps-freebsd/work/i3-${DISTVERSION} ./ > ~/i3-gaps-freebsd/files/extra-patch-gaps``.
