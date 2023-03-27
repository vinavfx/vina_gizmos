# Installation
1 - Copy to nuke folder
```sh
# Linux:
cd ~/.nuke
git clone --recursive https://github.com/vinavfx/vina_gizmos.git

# Windows
# Download git: https://git-scm.com/download/win
git clone --recursive https://github.com/vinavfx/vina_gizmos.git "C:\Users\<username>\.nuke\vina_gizmos"
````

2 - Copy this lines to <b>menu.py</b>

```python
import os

user_nuke = next(i for i in nuke.pluginPath() if '.nuke' in i)
vina_icon = '{}/vina_gizmos/icon.png'.format(user_nuke)
vina_gizmos = nuke.menu('Nodes').addMenu('Vina', icon=vina_icon)

vina_dir = '{}/vina_gizmos/gizmos'.format(user_nuke)

for g in os.listdir(vina_dir):
    vina_gizmos.addCommand(
        g.split('.')[0], lambda: nuke.createNode(os.path.join(vina_dir, g)), icon=vina_icon)
```
