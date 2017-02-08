# Thor Video Codec 

Implementation of [https://tools.ietf.org/html/draft-fuldseth-netvc-thor](https://tools.ietf.org/html/draft-fuldseth-netvc-thor)

This version has instant glitch patch (random prediction mode when decoding)

## Build

Windows: Use Visual Studio with build/Thor.sln.

Mac/Linux:

    make -j8

Binaries will appear in the build/ directory.

## Data preparation

Produce y4m:

    ffmpeg -i your_image_or_video -pix_fmt yuv420p raw_data.y4m
    
Encode:

    Thorenc -cf choose_one_config_file.txt -if raw_data.y4m -of encoded_data.bin
    
Decode:

    Thordec encoded_data.bin raw_data_result.y4m
    
Convert back to Image:

    ffmpeg -i raw_data_result.y4m image.png

## Usage

encoder:        Thorenc -cf config.txt -if in.yuv -of str.bit -rf out.yuv -qp N -width [width] -height [height] -f [framerate] -stat out.stat -qp [quant] -n [num frames]

A y4m file can be provided for input, and it will override width, height and framerate values given on the command-line.

decoder:        Thordec str.bit out.dec.yuv

