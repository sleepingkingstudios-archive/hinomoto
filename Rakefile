# Rakefile

task :default => :manifest

task :manifest do
  root_path = File.dirname __FILE__
  
  root = {}
  Dir[root_path + "/**/*.yml"].each do |path|
    path = path.gsub(/^#{root_path}/, '')
    segments = path.split(/[\/\\]/).tap { |ary| ary.delete "" }
    
    cll = root
    segments.each do |segment|
      segment =~ /.yml$/ ?
        cll[segment] = nil :
        cll = (cll[segment] ||= {})
    end # each
  end # each
  
  manifest_path = File.join root_path, 'manifest.yml'
  File.write manifest_path, root.to_yaml
end # task