# PAPERVIEW

A high performance animated desktop background setter for X11 that won't set your CPU on fire,
drain your laptop battery, or lower ya vidya game FPS.

![](screenshot.png)

Video of the above screenshot: https://www.youtube.com/watch?v=6ZTiA885bWM


## Build

### arch

    pacman -S sdl2
    make

### nix

    nix-shell -p gnumake SDL2 --command make


## Use

Command line:

    ./paperview FOLDER SPEED

A lower SPEED number will result in a faster frame rate. Only bitmap files are supported.
Creating your own bitmap folders from gifs requires imagemagick. For example, creating
a castle folder from castle.gif which you downloaded:

    mkdir castle
    mv castle.gif castle
    cd castle
    convert -coalesce castle.gif out.bmp


## Performance

Running on a Thinkpad X230 from 2012 at 1920x1080 and 60fps:

    intel_gpu_time ./paperview castle 5

    user: 1.904135s, sys: 0.357277s, elapsed: 100.458648s, CPU: 2.3%, GPU: 11.7%


## Known Issues

Picom (and possibly simliar compositors) seem to overwrite the base root X11 window.
A pure X11 workaround can be found here:

https://gist.github.com/AlecsFerra/ef1cc008990319f3b676eb2d8aa89903
