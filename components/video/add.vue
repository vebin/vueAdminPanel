<template>
    <div class="card">
        <div class="card-header">
            <strong><i class="fa fa-cloud-upload"></i> 上传视频</strong>
        </div>
        <div class="card-block">
            <div class="alert alert-info" role="alert">
                <strong>请求信息:</strong> {"code": "A00000", "data": {"upload_url": "http://220.181.184.157/upload",
                "file_id": "4004551398f84a38a371e107f099d27e"}}
            </div>
            <form>
                <fieldset class="form-group">
                    <label for="title">标题</label>
                    <input type="text" class="form-control" id="title" placeholder="请输入视频大标题">
                    <small class="text-muted">这个标题是显示在视频页面首页的</small>
                </fieldset>
                <fieldset class="form-group">
                    <label for="title">英文标题</label>
                    <input type="text" class="form-control" id="title" placeholder="请输入视频英文标题">
                    <small class="text-muted">若视频有英文标题请输入,若没有请留空</small>
                </fieldset>
                <fieldset class="form-group">
                    <label for="category">选择分类</label>
                    <div class="row">
                        <div class="col-xs-4">
                            <select class="c-select">
                                <option>电影</option>
                                <option>电视</option>
                                <option>宣传片</option>
                                <option>纪录片</option>
                                <option>活动</option>
                            </select>
                        </div>
                        <div class="col-xs-4">
                            <div class="input-group">
                                <input type="text" class="form-control" id="exampleInputAmount" placeholder="添加新分类">
                                <a class="input-group-addon btn btn-primary">增加分类</a>
                            </div>
                        </div>
                        <div class="col-xs-4">
                            <div class='input-group date' id='datetimepicker10'>
                                <input type='text' class="form-control" placeholder="影片拍摄时间"/>
                                <div class="input-group-addon"><i class="fa fa-calendar"></i></div>
                            </div>
                        </div>
                    </div>
                    <small class="text-muted">请选择最新分类</small>
                </fieldset>
                <fieldset class="form-group">
                    <label for="category">上传封面图</label>
                    <Uploadvideocover></Uploadvideocover>
                    <small class="text-muted">上传图片质量限制在800Kb,最佳分辨率300px × 300px</small>
                </fieldset>
                <fieldset class="form-group uploadForm">
                    <label for="category">上传视频</label>
                    <Uploadvideos></Uploadvideos>
                    <small class="text-muted">请选择需要上传的视频文件,单个上传大小无限制</small>
                </fieldset>
                <fieldset class="form-group">
                    <label for="category">请描述视频内容</label>
                    <textarea id="editor" placeholder="Enter text ..." style=""></textarea>
                    <small class="text-muted">使用编辑器编辑的格式会被视频展示页忽略,指接受纯文本信息</small>
                </fieldset>
                <button type="submit" class="btn btn-primary">开始上传</button>
            </form>
        </div>
    </div>

</template>

<script type="text/babel">
    import Uploadvideocover from './uploadvideocover.vue'
    import Uploadvideos from './uploadvideos.vue'

    export default{
        ready(){
            tinymce.init({
                selector: '#editor',
                plugins: "image imagetools",
                height: 220
            });
            $('#datetimepicker10').datetimepicker({
                viewMode: 'years',
                format: 'MM/YYYY'
            });
        },
        beforeDestroy(){
            tinymce.remove("#editor");
        },
        components:{
            Uploadvideocover,
            Uploadvideos
        }
    }
</script>

<style lang="sass?outputStyle=expanded">
</style>