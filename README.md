百度UEditor
===========

### 安装
Either run

```
$ php composer.phar require qschen2/ueditor "*"
```

or add

```
"qschen2/ueditor": "*"
```

to the ```require``` section of your `composer.json` file.

### 应用

controller:  

```
public function actions()
{
    return [
        'upload' => [
            'class' => 'qschen2\ueditor\UEditorAction',
        ]
    ];
}
```

view:  

```
echo \qschen2\ueditor\UEditor::widget([]);
```

或者：

```
echo $form->field($model,'colum')->widget('qschen2\ueditor\UEditor',[]);
```
### 配置相关

##### 编辑器相关配置，请在`view` 中配置，参数为`clientOptions`，比如定制菜单，编辑器大小等等，具体参数请查看[UEditor官网文档](http://fex-team.github.io/ueditor/)。

简单实例:  
```php
use \qschen2\ueditor\UEditor;
echo UEditor::widget([
    'clientOptions' => [
        //编辑区域大小
        'initialFrameHeight' => '200',
        //定制菜单
        'toolbars' => [
            [
                'fullscreen', 'source', 'undo', 'redo', '|',
                'fontsize',
                'bold', 'italic', 'underline', 'fontborder', 'strikethrough', 'removeformat',
                'formatmatch', 'autotypeset', 'blockquote', 'pasteplain', '|',
                'forecolor', 'backcolor', '|',
                'lineheight', '|',
                'indent', '|'
            ],
        ]
]);
```

##### 文件上传相关配置，请在`controller`中配置，参数为`config`,例如文件上传路径等；更多参数请参照 [config.php](https://github.com/Bigqschen2/yii2-ueditor-widget/blob/master/config.php) (跟UEditor提供的config.json一样)

简单实例:  
```php
public function actions()
{
    return [
        'upload' => [
            'class' => 'qschen2\ueditor\UEditorAction',
            'config' => [
                "imageUrlPrefix"  => "http://www.baidu.com",//图片访问路径前缀
                "imagePathFormat" => "/upload/image/{yyyy}{mm}{dd}/{time}{rand:6}" //上传保存路径
            ],
        ]
    ];
}
```
