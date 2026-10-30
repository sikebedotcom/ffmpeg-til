# 音声から動画を作成する

## 音声に黒背景の動画をつける

ffmpeg -f lavfi -i color=c=black:s=640x480 -i input_audio.mp3 -vcodec libx264 -acodec copy -pix_fmt yuv420p -shortest output.mp4

mp3やaacのような既に圧縮済みのファイルであればさほど容量を喰わないし余計な変換を挟まないため音声コーデックはコピーにしている
元音声がWAVEの場合は`-acodec copy`の部分をmp3なりAACなりにすると容量を節約できる
OpusにするのはWAVEかつ元々サンプルレート48khzの場合のほうが良いかもしれない

## 参考
https://azelpg.gitlab.io/azsky2/note/ffmpeg/filter.html
https://dev.classmethod.jp/articles/ffmpeg-create-movie-by-audio/
https://xxxmammom2410.hatenablog.com/entry/2023/08/13/223134
